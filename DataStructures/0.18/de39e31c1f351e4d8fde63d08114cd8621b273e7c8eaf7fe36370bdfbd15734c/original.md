```
isequal(sc1,sc2)
```

Checks if two containers are equal in the sense that they contain the same items; the keys are compared using the `eq` method, while the values are compared with the `isequal` function. In the case of SortedMultiDict, equality requires that the values associated with a particular key have same order (that is, the same insertion order). Note that `isequal` in this sense does not imply any correspondence between semitokens for items in `sc1` with those for `sc2`. If the equality-testing method associated with the keys and values implies hash-equivalence in the case of SortedDict, then `isequal` of the entire containers implies hash-equivalence of the containers. Time: O(*cn* + *n* log *n*)
