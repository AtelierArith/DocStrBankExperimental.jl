```
pkstruct(M, N; fast = false, atol1::Real = 0, atol2::Real = 0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ) -> KRInfo
```

行列ペンシル `M-λN` のクロンネッカー構造情報を決定し、`KRInfo` オブジェクトを返します。

右クロンネッカー指標 `rki`、左クロンネッカー指標 `lki`、無限の基本除数 `id`、有限固有値の数 `nf` および正規ランク `nrank` は、それぞれ `KRInfo.rki`、`KRInfo.lki`、`KRInfo.id`、`KRInfo.nf` および `KRInfo.nrank` から取得できます。クロンネッカー構造情報の決定は、ペンシル `M-λN` を、ペンシル `M-λN` のすべての構造要素を示す適切なクロンネッカー様形式 (KLF) に減少させることによって行われます。減少は直交類似変換を使用して行われ、`fast = true` の場合は列ピボッティングを伴うランクを明らかにするQR分解に基づくランク決定、または `fast = false` の場合はより信頼性の高いSVD分解に基づいて行われます。効率のために、減少は部分的にのみ行われ、実行された直交変換は累積されません。

右クロンネッカー指標は整数ベクトル `rki` に提供され、各 `i` 番目の要素 `rki[i]` はサイズ `k x (k+1)` の基本クロンネッカーブロックの行次元 `k` です。 `rki` の要素数はペンシル `M-λN` の右零空間の次元であり、その合計は右最小多項式零空間基底の次数です。

左クロンネッカー指標は整数ベクトル `lki` に提供され、各 `i` 番目の要素 `lki[i]` はサイズ `(k+1) x k` の基本クロンネッカー ブロックの列次元 `k` です。 `lki` の要素数はペンシル `M-λN` の左零空間の次元であり、その合計は左最小多項式零空間基底の次数です。

無限固有値の重複度は整数ベクトル `id` に提供され、各 `i` 番目の要素 `id[i]` は無限基本除数の次数 (すなわち、無限固有値の重複度) です。 `id` の要素数はペンシル `M-λN` の無限基本除数の数です。

正規ランク `nrank` は、すべての値の `λ` に対する `M-λN` の最大ランクです。 `N = nothing` の場合、`nrank` は `M` のランクです。

キーワード引数 `atol1`、`atol2` および `rtol` は、それぞれ `M` の非ゼロ要素の絶対許容誤差、`N` の非ゼロ要素の絶対許容誤差、および `M` と `N` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `M` の最小次元のサイズ、`ϵ` は `M` の要素型の機械イプシロンです。
