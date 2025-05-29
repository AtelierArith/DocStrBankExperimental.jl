```
SecondOrderddt{EM, SO, SI, IT, BT} <: AbstractApproximationModel
```

ツール `d/dt` で使用される二次近似モデルです。これは、過大評価と過小評価の両方に使用できます。

### フィールド

  * `oa`      – （オプション、デフォルト: `true`）過大評価と過小評価の選択フラグ
  * `exp`     – （オプション、デフォルト: `BaseExp`）指数法
  * `setops`  – （オプション、デフォルト: `:lazy`）集合演算法
  * `sih`     – （オプション、デフォルト: `:concrete`）対称区間ハルを計算する方法
  * `inv`     – （オプション、デフォルト: `false`）`true` の場合、状態行列が可逆であると仮定し、`Φ` 関数でその逆行列を使用します
  * `backend` – （オプション、デフォルト: `nothing`）アルゴリズムが具体的な多面体計算を適用する必要がある場合に使用されます

### アルゴリズム

変換は次のとおりです：

  * $$
    Φ ← \exp(Aδ)
    $$

    ,
  * $$
    Ω_0 ← bloat(CH(\mathcal{X}_0, Φ\mathcal{X}_0), ε)
    $$

ここで、$bloat(\mathcal{X}, ε)$ は集合 $\mathcal{X}$ を値 $ε$ で膨張させます。`oa == false` の場合、膨張は逆の方法で作用し、集合を縮小します。

### 参考文献

E. Asarin, T. Dang, O. Maler, O. Bournez: *近似的到達可能性解析の断片線形動的システム*. HSCC 2000.
