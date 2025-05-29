```
XPRS_NODESELECTION
```

Branch and Bound: This determines which nodes will be considered for solution once the current node has been solved. (integer)

Default value: Dependent on the matrix characteristics.

Values: 1 : Local first: Choose between descendant and sibling nodes if available; choose from all outstanding nodes otherwise. 2 : Best first: Choose from all outstanding nodes. 3 : Local depth first: Choose between descendant and sibling nodes if available; choose from the deepest nodes otherwise. 4 : Best first, then local first: Best first is used for the first BREADTHFIRST nodes, after which local first is used. 5 : Pure depth first: Choose from the deepest outstanding nodes.
