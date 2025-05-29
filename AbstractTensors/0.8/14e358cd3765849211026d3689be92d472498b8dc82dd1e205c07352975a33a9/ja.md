```
@co fun(args...)
```

マクロ `@co` を使用して、任意の関数の擬似スカラー `complement` バリアントを作成します：

```Julia
julia> @co myfun(x)
comyfun (generic function with 1 method)
```

これで `comyfun(x) = complementleft(myfun(complementright(x)))` が定義されました。

```Julia
julia> @co myproduct(a,b)
comyproduct (generic function with 1 method)
```

これで `comyproduct(a,b) = complementleft(myproduct(!a,!b))` が定義されました。
