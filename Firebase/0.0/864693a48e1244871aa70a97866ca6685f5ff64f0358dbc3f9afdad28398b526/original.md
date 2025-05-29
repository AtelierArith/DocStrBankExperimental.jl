firestore_partitionquery(url)

Partitions a query by returning partition cursors that can be used to run the query in parallel. The returned partition cursors are  split points that can be used by documents.runQuery as starting/end points for the query results.
