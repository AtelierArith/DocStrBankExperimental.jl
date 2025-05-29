```
@jaccel [name][, clauses...]
```

アクセラレータコンテキストを作成します。

`name`が指定されていない場合、このコンテキストは現在アクティブなコンテキストとしてのみアクセスできます。

# 引数

  * `name`::String: このアクセラレータコンテキストのユニークな名前
  * `framework`::NamedTuple:
  * `device`::Integer:
  * `compiler`::Integer:
  * `machine`::Integer:
  * `constant`::Tuple of Variable literal :
  * `set`::Named Tuple:

[`@jdecel`](@jdecel)や[`@jkernel`](@jkernel)も参照してください。

# 例

```julia-repl
julia> @jaccel myacc framework(fortran="gfortran -fPIC -shared -g")
AccelInfo
```

# 実装

T.B.D. ```
