```
delayembed(X, numdelays::Int)

delay embedding for data, should return
Xemb: ((numdelays)⋅n) × (m - numdelays - 1) data array

# '' appears to work for the following:
# testMat = [1 2 3 4 5 6 ; 7 8 9 10 11 12 ; 13 14 15 16 17 18];
# k = 0, 1, 2, 3
# delayembed(testMat,k)
# delayembed(testMat,0) == testMat '' 

Arguments
=================
- X: n × m data array with n spatial points and m timepoints
- numdelays: integer, number of delays (should be that q = 1 is no delays for consistency)
```
