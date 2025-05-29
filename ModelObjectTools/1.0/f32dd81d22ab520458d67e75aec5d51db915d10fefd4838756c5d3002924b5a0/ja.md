```
@modef typedef
```

これは、Baseで定義された@kwdefヘルパーマクロのわずかな修正です。これが適用される構造体が、このパッケージで定義された関数と効果的に使用できることを保証します。具体的には：(1) すべてのフィールドはデフォルト値を持たなければならず、そうでない場合はマクロがエラーを投げます；(2) Base.@kwdefと同様のスタイルでオプションのキーワード引数を持つコンストラクタを自動的に作成しますが、さらにそのコンストラクタは、addVarInfo()を介して変数名を登録することによって定義されたすべてのパラメータが有効であるかどうかをチェックします。

# 例

```julia-repl
julia> @modef struct ModelParams
                  myScalarParam::Float64 = 4.0
                  myVecParam::Vector{Float64} = [1.0, 2.0]
              end
ModelParams

julia> addVarInfo(:myScalarParam; lb = 0.0); addVarInfo(:myVecParam; normalization = :ordered);

julia> ModelParams()
ModelParams(4.0, [1.0, 2.0])

julia> ModelParams(myVecParam = [2.0, 1.0])
ERROR: [2.0, 1.0] is not a valid input for myVecParam.
Stacktrace:
[...]
```
