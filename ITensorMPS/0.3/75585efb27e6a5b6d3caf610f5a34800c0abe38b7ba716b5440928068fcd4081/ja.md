```
contract(ψ::MPS, A::MPO; kwargs...) -> MPS
*(::MPS, ::MPO; kwargs...) -> MPS

contract(A::MPO, ψ::MPS; kwargs...) -> MPS
*(::MPO, ::MPS; kwargs...) -> MPS
```

`MPO` `A` と `MPS` `ψ` を収束させ、`MPO` のユニークなサイトインデックスを持つ `MPS` を返します。

例えば、プライムレベルが1と0のサイトインデックスを持つMPO `-s'-A-s-` と、プライムレベルが0のサイトインデックスを持つMPS `-s-x` の場合、結果はプライムレベルが1のサイトインデックスを持つMPS `y` であり、`-s'-y = -s'-A-s-x` となります。

プライムレベルが1と0のMPOをプライムレベルが0のMPSと収束させ、結果としてプライムレベルが0のMPSを得ることが一般的であるため、便利な関数 `apply` を提供します：

```julia
apply(A, x; kwargs...) = replaceprime(contract(A, x; kwargs...), 2 => 1)`.
```

`method` キーワードを使ってメソッドを選択します。例えば、`"densitymatrix"` や `"naive"` です。

# キーワード

  * `cutoff::Float64=1e-13`: 密度行列の固有値を切り捨てるためのカットオフ値。デフォルトはやや恣意的で変更される可能性があるため、一般的には `cutoff` 値を設定するべきです。
  * `maxdim::Int=maxlinkdim(A) * maxlinkdim(ψ))`: 結果のMPSの最大ボンド次元。
  * `mindim::Int=1`: 結果のMPSの最小ボンド次元。
  * `normalize::Bool=false`: 結果のMPSを正規化するかどうか。
  * `method::String="densitymatrix"`: 収束に使用するアルゴリズム。現在のオプションは「densitymatrix」で、MPOとMPSによって形成されたネットワークが二乗され、各サイトで反復的に対角化される密度行列に収束されるものと、「naive」で、MPOとMPSテンソルが各サイトで正確に収束され、その後結果のMPSの切り捨てが行われるものです。

[`apply`](@ref) も参照してください。
