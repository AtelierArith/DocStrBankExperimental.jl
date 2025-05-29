```
Bucklin <: VotingSystem
```

A Bucklin voting system object.In the Bucklin voting system, points are added for each candidate in an iterative manner until the point value of a candidate exceeds 50% of the number of voters. In the first round, each candidate recieves a point for each first rank preference.  If the candidate with the most points does not exceed 50%, the candidates recieve a point for each second rank vote, and so forth until a candidate exceeds the 50% point threshold.  
