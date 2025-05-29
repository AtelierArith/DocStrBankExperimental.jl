`stability_region(z, tab::ODERKTableau; embedded = false)`

タブローから `z` における安定性関数を計算します。安定であれば <1 です。`embedded = true` の場合、埋め込み法のための安定性関数が計算されます。それ以外の場合、主法のための安定性関数が計算されます（デフォルト）。

$$
r(z) = 1 + z bᵀ(I - zA)⁻¹ e
$$

ここで、e は1のベクトルを表します。
