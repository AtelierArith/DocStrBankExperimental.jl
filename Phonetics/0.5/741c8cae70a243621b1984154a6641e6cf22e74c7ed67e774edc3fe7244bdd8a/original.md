```
distinctiveness(s, corpus; [method=:dtw, dist=SqEuclidean(), radius=10, reduction=mean])
```

Calculates the acoustic distinctiveness of `s` given the corpus `corpus`. The `method`, `dist`, and `radius` arguments are passed into `acdist`. The `reduction` argument can be any function that reduces an iterable to one number, such as `mean`, `sum`, or `median`. 

For more information, see Kelley (2018, September, How acoustic distinctiveness affects spoken word recognition: A pilot study, DOI: 10.7939/R39G5GV9Q) and Kelley & Tucker (2018, Using acoustic distance to quantify lexical competition, DOI: 10.7939/r3-wbhs-kr84).
