```
hausdorff_distance(X::LazySet{N}, Y::LazySet{N}; [p]::N=N(Inf),
                   [ε]=N(1e-3)) where {N}
```

与えられた閾値までの2つの凸集合間のハウスドルフ距離を計算します。

### 入力

  * `X` – 凸集合
  * `Y` – 凸集合
  * `p` – （オプション、デフォルト: `Inf`）ハウスドルフ距離のノルムパラメータ
  * `ε` – （オプション、デフォルト: `1e-3`）精度の閾値; 真のハウスドルフ距離は結果からこの値までの乖離を許容されます

### 出力

$$
X
$$

と$Y$の間のハウスドルフ距離の$ε$-近傍からの値。

### 注意事項

$$
p
$$

-ノルムが与えられた場合、集合$X$と$Y$の間のハウスドルフ距離$d_H^p(X, Y)$は次のように定義されます：

$$
    d_H^p(X, Y) = \inf\{δ ≥ 0 \mid Y ⊆ X ⊕ δ 𝐵_p^n \text{ and } X ⊆ Y ⊕ δ 𝐵_p^n\}
$$

ここで$𝐵_p^n$は$p$-ノルムにおける$n$次元単位球です。

実装は内部的に$X$と$Y$のサポート関数に依存する可能性があるため、サポート関数の実装における不正確さが結果に影響を与える可能性があります。執筆時点では、不正確なサポート関数を持つ唯一の凸集合タイプは遅延[`Intersection`](@ref)です。

### アルゴリズム

ハウスドルフ距離を区間$[l, u]$で制限するために二分探索を行います。初期状態では$l$は$0$、$u$は以下に説明されるように設定されます。二分探索は$u - l ≤ ε$となったとき、すなわち区間が十分に小さくなったときに終了します。

上限$u$を見つけるために、軸平行方向での最大距離を取るというヒューリスティックから始めます。この境界が機能しない限り、境界を$2$ずつ増加させます。

値$δ$が与えられた場合、集合がハウスドルフ距離$δ$以内にあるかどうかを確認するために、上記の包含関係を単純にチェックします。右辺では遅延`Bloating`を使用します。
