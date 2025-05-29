```
@pseudo fun(args...)
```

マクロ `@pseudo` を使用して、任意の関数の擬似スカラー `complement` バリアントを作成します：

```Julia
julia> @pseudo myfun(x)
pseudomyfun (generic function with 1 method)
```

これで `pseudomyfun(x) = complementleft(myfun(complementright(x)))` が定義されました。

```Julia
julia> @pseudo myproduct(a,b)
pseudomyproduct (generic function with 1 method)
```

これで `pseudomyproduct(a,b) = complementleft(myproduct(!a,!b))` が定義されました。
