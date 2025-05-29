```
gettransmat(seq; relabel = false) -> (Dict, Matrix)
```

ラベルシーケンス `seq` に関連付けられた遷移行列を返します。ラベルは正の整数でなければなりません。

**引数**

  * `seq::Vector{<:Integer}`: 正のラベルシーケンス。

**キーワード引数**

  * `relabel::Bool = false`: true に設定すると、シーケンスが連続的になります。例えば、`[7,7,9,9,1,1]` は `[2,2,3,3,1,1]` になります。

**出力**

  * `Dict{Integer,Integer}`: 元のラベルと新しいラベルの間のマッピング。
  * `Matrix{Float64}`: 遷移行列。
