```
nsingular(
    result;
    counting_multiplicities = false,
    kwargs...,
)
```

特異解の数。解は、その巻数が1より大きいか、条件数が`tol`より大きい場合に特異と見なされます。`counting_multiplicities=true`の場合、特異解の数にその重複度を掛けたものが返されます。
