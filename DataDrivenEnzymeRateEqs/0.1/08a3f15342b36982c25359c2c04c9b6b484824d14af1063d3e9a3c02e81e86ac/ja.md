```
derive_general_mwc_rate_eq(metabs_and_regulators_kwargs...)
```

一般的なMWC速度方程式を使用して反応速度を計算する関数を導出します。これは、特定の触媒または調節部位に結合する基質、生成物、および調節因子のリストを使用します。

一般的なMWC速度方程式は次のように表されます：

$$
Rate = \frac{{V_{max}^a \prod_{i=1}^{n} \left(\frac{S_i}{K_{a, i}}\right) - V_{max, rev}^a \prod_{i=1}^{n} \left(\frac{P_i}{K_{a, i}}\right) \cdot Z_{a, cat}^{n-1} \cdot Z_{a, reg}^n + L \left(V_{max}^i \prod_{i=1}^{n} \left(\frac{S_i}{K_{i, i}}\right) - V_{max, rev}^i \prod_{i=1}^{n} \left(\frac{P_i}{K_{i, i}}\right)\right) \cdot Z_{i, cat}^{n-1} \cdot Z_{i, reg}^n}}{Z_{a, cat}^n \cdot Z_{a, reg}^n + L \cdot Z_{i, cat}^n \cdot Z_{i, reg}^n}
$$

ここで：

  * $$
    V_{max}^a
    $$

    は前向き反応の最大速度
  * $$
    V_{max, rev}^a
    $$

    は逆反応の最大速度
  * $$
    V_{max}^i
    $$

    は前向き反応の最大速度
  * $$
    V_{max, rev}^i
    $$

    は逆反応の最大速度
  * $$
    S_i
    $$

    は $i^{th}$ 基質の濃度
  * $$
    P_i
    $$

    は $i^{th}$ 生成物の濃度
  * $$
    I_i
    $$

    は $i^{th}$ 触媒部位阻害剤の濃度
  * $$
    R_i
    $$

    は $i^{th}$ アロステリック調節因子の濃度
  * $$
    K_{a, X}
    $$

    は活性MWC状態に対する $X$ 代謝物の結合定数
  * $$
    K_{i, X}
    $$

    は不活性MWC状態に対する $X$ 代謝物の結合定数
  * $$
    Z_{a, cat}
    $$

    は活性MWC状態における触媒部位のアロステリック因子
  * $$
    Z_{i, cat}
    $$

    は不活性MWC状態における触媒部位のアロステリック因子
  * $$
    Z_{a, reg}
    $$

    は活性MWC状態における調節部位のアロステリック因子
  * $$
    Z_{i, reg}
    $$

    は不活性MWC状態における調節部位のアロステリック因子
  * $$
    L
    $$

    はリガンドが存在しない場合の不活性と活性酵素構造の比率
  * $$
    n
    $$

    は酵素のオリゴマー状態

# 引数

  * `metabs_and_regulators_kwargs...`: 反応の基質、生成物、触媒部位、調節部位、およびその他のパラメータを指定するキーワード引数。

# 戻り値

  * 一般的なMWC速度方程式を使用して反応速度を計算する関数
  * 速度方程式で使用される代謝物とパラメータの名前のタプル

```
