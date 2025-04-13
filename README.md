### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 12/04/2025 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:

```
import pandas as pd
import matplotlib.pyplot as plt

# 1. Read the data from a CSV file
file_path = 'clustervisitor.csv'  
try:
    data = pd.read_csv(file_path)  
except FileNotFoundError:
    print(f"Error: File not found at '{file_path}'. Please check the file path.")
    exit()

# 2. Define Age Groups
age_groups = {
    'Young': (data['Age'] <= 35),  # Young: 35 and below
    'Middle': (data['Age'] > 30) & (data['Age'] <= 50),  # Middle: 36 to 55
    'Elder': (data['Age'] > 50)  # Elder: Above 55
}

# 3. Segment Visitors based on Age Groups
data['Age Group'] = 'Unknown'
for group, condition in age_groups.items():
    data.loc[condition, 'Age Group'] = group

# 4. Create a list to store counts of visitors in each age group
age_group_counts = data['Age Group'].value_counts()

# 5. Visualize the result
age_group_labels = age_group_counts.index
visitor_counts = age_group_counts.values

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

![Screenshot 2025-04-12 141709](https://github.com/user-attachments/assets/1f3f9958-0137-4cb1-a778-f2316ee1deb0)

### Result:
After executing the program, the visitor data was successfully segmented into age groups. A bar chart was generated to visualize the number of visitors in each age category.
