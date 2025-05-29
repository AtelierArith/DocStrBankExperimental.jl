```
@jlaunch [kernelname, [accelname, ]][clauses...]
```

アクセラレータ上でカーネルを起動します。

`kernelname` または `accelname` が指定されていない場合、現在アクティブなアクセラレータまたはカーネルコンテキストが使用されます。

# 引数

  * `kernelname`::String: カーネルコンテキスト名
  * `accelname`::String: アクセルコンテキスト名

他にも [`@jaccel`](@jaccel)、[`@jkernel`](@jkernel) を参照してください。

# 例

```julia-repl
julia> @jlaunch mykernel myaccel input(X, Y) output(Z)
0
```

# 実装

T.B.D.
