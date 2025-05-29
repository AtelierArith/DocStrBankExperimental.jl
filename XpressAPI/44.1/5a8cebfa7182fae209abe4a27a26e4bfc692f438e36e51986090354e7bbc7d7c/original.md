```
XPRS_VARSELECTION
```

Branch and Bound: This determines the formula used to calculate the estimate of each integer variable, and thus which integer variable is selected to be branched on at a given node. (integer)

The variable selected to be branched on is the one with the maximum estimate.

Default value: `-1`

Values: -1 : Determined automatically. 1 : The minimum of the 'up' and 'down' pseudo costs. 2 : The 'up' pseudo cost plus the 'down' pseudo cost. 3 : The maximum of the 'up' and 'down' pseudo costs, plus twice the minimum of the 'up' and 'down' pseudo costs. 4 : The maximum of the 'up' and 'down' pseudo costs. 5 : The 'down' pseudo cost. 6 : The 'up' pseudo cost. 7 : A weighted combination of the 'up' and 'down' pseudo costs, where the weights depend on how fractional the variable is. 8 : The product of the 'up' and 'down' pseudo costs.
