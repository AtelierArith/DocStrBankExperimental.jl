```
FunctionTerm{Forig,Fanon,Names} <: AbstractTerm
```

これはJulia関数への呼び出しを表します。最初の型パラメータは、元々指定された関数の型（例：`typeof(log)`）であり、2番目はデータテーブルに要素ごとに適用される無名関数の型です。

`FunctionTerm`は、元の呼び出しの引数もキャプチャし、それらを特別なDSL呼び出しの一部であるかのように解析します。これにより、`*`を展開し、`&`を`+`に分配し、シンボルを`Term`でラップするルールが適用されます。

元の関数を型パラメータとして保存し、引数を特別なDSL呼び出しの一部であるかのように悲観的に解析することで、カスタム構文を最小限の追加労力でサポートできるようになります。パッケージは`apply_schema(f::FunctionTerm{typeof(special_syntax)}, schema, ::Type{<:MyModel})`でディスパッチし、`f.args_parsed`から解析された引数を取り出して独自のカスタムタームを構築できます。

# フィールド

  * `forig::Forig`: 元の関数（例：`log`）
  * `fanon::Fanon`: 生成された無名関数（例：`(a, b) -> log(1+a+b)`）
  * `exorig::Expr`: `@formula`に渡された元の式
  * `args_parsed::Vector`: `@formula`に渡された呼び出しの引数で、各引数は「特別な」DSL呼び出しであるかのように解析されます。

# 型パラメータ

  * `Forig`: 元の関数の型（例：`typeof(log)`）
  * `Fanon`: 生成された無名関数の型
  * `Names`: 無名関数への引数の名前（`NTuple{N,Symbol}`として）

# 例

```jldoctest
julia> f = @formula(y ~ log(1 + a + b))
FormulaTerm
Response:
  y(unknown)
Predictors:
  (a,b)->log(1 + a + b)

julia> typeof(f.rhs)
FunctionTerm{typeof(log),var"#1#2",(:a, :b)}

julia> f.rhs.forig(1 + 3 + 4)
2.0794415416798357

julia> f.rhs.fanon(3, 4)
2.0794415416798357

julia> modelcols(f.rhs, (a=3, b=4))
2.0794415416798357

julia> modelcols(f.rhs, (a=[3, 4], b=[4, 5]))
2-element Array{Float64,1}:
 2.0794415416798357
 2.302585092994046
```
