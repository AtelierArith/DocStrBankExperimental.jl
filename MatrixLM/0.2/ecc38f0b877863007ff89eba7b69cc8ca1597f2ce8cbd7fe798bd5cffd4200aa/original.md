```
RawData(response::Response, predictors::Predictors)
```

Type for storing response and predictor matrices

Also stores dimensions of matrices as n, m, p, and q. 

  * `n` : number of rows of X = number of rows of Y
  * `m` : number of rows of Z = number of columns of Y
  * `p` : number of columns of X
  * `q` : number of columns of Z

The constructor will compute n, m, p, and q based on the response and  predictor matrices and assert that they are consistent. 
