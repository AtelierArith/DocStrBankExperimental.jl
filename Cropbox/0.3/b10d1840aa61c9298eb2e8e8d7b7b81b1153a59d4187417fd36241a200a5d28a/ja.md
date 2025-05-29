```
instance(S; <キーワード引数>) -> S
```

システム `S` のインスタンスを、設定で指定された初期条件と追加オプションを使って作成します。

参照: [`@config`](@ref), [`simulate`](@ref)

# 引数

  * `S::Type{<:System}`: インスタンス化されるシステムの型。

# キーワード引数

  * `config=()`: システムのパラメータ値を含む設定。
  * `options=()`: `S` のコンストラクタに渡されるキーワード引数; 名前付きタプルが期待されます。
  * `seed=nothing`: 設定を解析しインスタンスを作成する前に初期化されるランダムシード。

# 例

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
           b(a) ~ accumulate
       end;

julia> instance(S)
S
  context = <Context>
  config = <Config>
  a = 1.0
  b = 0.0
```
