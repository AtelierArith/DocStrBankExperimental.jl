```
lc_primitivetype(o::Any)
```

Any型の最も低い共通プリミティブ型

#### 例:

```
julia> o = ([1//2, 1//3]; (1//4, 1//1, 1//6));
julia> lc_primitivetype(o)
Int64
```
