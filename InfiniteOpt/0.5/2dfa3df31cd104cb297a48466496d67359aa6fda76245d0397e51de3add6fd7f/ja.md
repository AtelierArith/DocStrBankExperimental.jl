```
DependentParameters{T <: InfiniteArrayDomain, 
                    M <: NonGenerativeDerivativeMethod} <: InfOptParameter
```

依存する無限パラメータのコレクションを格納するための `DataType`。

**フィールド**

  * `domain::T`: パラメータを特徴づける無限ドメイン。
  * `supports::Dict{Vector{Float64}, Set{DataType}}`: キーがサポートで、値が各サポートのラベルのセットであるサポート辞書。
  * `sig_digits::Int`: サポート値を丸めるために使用される有効桁数。
  * `derivative_methods::Vector{M}`: 各パラメータに関連付けられた導関数評価方法。
