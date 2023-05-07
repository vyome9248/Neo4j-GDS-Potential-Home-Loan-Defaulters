# Neo4j-GDS-Potential-Home-Loan-Defaulters
Neo4j-PySpark Proof of Concept
The data is made using the fake data generation notebook, you can make your data. (repo in my github)
You have to go to Neo4j, create a blank sandbox and use those credentials when running this notebook. (Bolt url and password from connection details).
The data manipulation is being done on Spark as it is difficult to do it on Neo4j, after the transformations, data is fed into Neo4j through Spark-Neo4j connection.
You need to install jar files in your Databricks compute to write data from Databricks to Neo4j, I have included the jar files in the repo.
The Graph Data Science Algorithms are run on the data ingested into Neo4j and the results of these algorithms are being streamed back to Databricks.
These results can be used to augment our dataset and make direct inferences as well.
If you want to see the graphs on Neo4j, you have to write cypher queries in Neo4j.
Cypher query to check similarity graph between Defaulters and Non Defaulters -> match (n:Defaulters)-[r:SIMILAR]->(m:`Non Defaulters`)  return n,r,m

PS. Notebook Optimization Tip -> The connection is being made again and again to write, stream data back and forth between Databricks and Neo4j. You can make a variable with the connection details and use that everywhere, otherwise you need to make bolt url and password changes throughout the notebook.
