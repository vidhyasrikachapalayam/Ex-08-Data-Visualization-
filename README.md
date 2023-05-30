# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sbn

df=pd.read_csv("/content/Superstore(1).csv",encoding='windows-1252')

df.head()

df.info()

df.isnull().sum()

1.Which Segment has Highest sales?

sbn.barplot(x=df['Segment'],y=df['Sales'])

plt.title("Highest Sales of the segment")

2.Which City has Highest profit?

sbn.barplot(x=df['City'],y=df['Profit'])

plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]

df.head(5)

City=City.groupby(by=["City"]).sum().sort_values(by="Profit")

plt.figure(figsize=(10,10))

sbn.barplot(x=City.index,y="Profit",data=City)

plt.xticks(rotation = 90)

plt.xlabel=("City")

plt.ylabel=("Profit")


plt.show()

3.Which ship mode is profitable?

sbn.barplot(x=df['Ship Mode'],y=df['Profit'])

plt.title("Profitable Ship Mode")

4.Sales of the product based on region.

sbn.barplot(x=df['Sales'], y=df['Region'])

plt.title("Sales of Product based on Region")

5.Find the relation between sales and profit.

sbn.lineplot(x=df['Sales'], y=df['Profit'])

plt.title("Relation between Sales and Profit")

6.Find the relation between sales and profit based on the following category. i) Segment ii)City iii)States iv)Segment and Ship Mode

v)Segment, Ship mode and Region 

i) Segment

grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.title("Sales and Profit based on Segment")
plt.show()

2.City
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('City')

ax.set_ylabel('Value')

ax.legend()

plt.title("Sales and Profit based on City")

plt.show()

3.states

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('State')

ax.set_ylabel('Value')

ax.legend()

plt.title("Sales and Profit based on States")

4.Segment and Ship Mode

grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

pivot_data.plot(kind='bar', ax=ax)

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

plt.legend(title='Ship Mode')

plt.legend(loc="best")

plt.title("Sales and Profit based on Segment and Ship mode")

plt.show()

5.Segment, Ship mode and Region

grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])

sbn.set_style("whitegrid")

sbn.set_palette("Set1")

pivot_data.plot(kind='bar', stacked=True, figsize=(8, 5))

plt.legend(title='Region')

plt.legend(loc='best')

plt.title("Sales and Profit based on Segment,Ship mode and Region")

# OUPUT
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/dd8a6b2d-1b56-4bb6-b699-fd32cbc71a97)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/7e9601e8-0adf-4e55-8f69-d0ac6de6a828)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/dae54de2-8233-4d84-bd5c-ea462bae7e66)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/511093a9-7c91-4b4d-9ec4-1941f2be7743)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/f7f03a9f-5b6f-4e7f-aec9-4c8286b11602)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/f5016371-fd33-41b6-98df-17cd1bf14527)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/1b7c8548-c648-417b-8e09-090ec7400b7a)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/c33805ca-ab25-47a5-8c04-5fd88d8e9631)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/ec0e60ef-bb44-4a42-947f-d1a0a7951194)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/e064bd83-3ec3-44b8-8677-9313f99f1df0)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/fa92f432-8596-4116-aa58-864681573dd7)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/08bdcfb6-07ce-4096-84e0-e50184f407de)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/c30b5f80-2934-48a7-99b2-5aec9e93451f)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/7975b055-c7ce-4333-b842-64841424f87e)
![image](https://github.com/vidhyasrikachapalayam/Ex-08-Data-Visualization-/assets/119477817/6f3bce25-7ab2-4350-9a5e-91ad9d49135a)



