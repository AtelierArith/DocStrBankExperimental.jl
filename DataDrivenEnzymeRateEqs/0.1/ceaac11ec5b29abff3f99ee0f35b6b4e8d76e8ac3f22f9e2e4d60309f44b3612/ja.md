```
derive_general_qssa_rate_eq(metabs_and_regulators_kwargs...)
```

反応の基質、生成物、および調節因子のリストを使用して、準定常状態近似（QSSA）を用いて反応速度を計算する関数を導出します。

一般的なQSSA速度方程式は次のように表されます：

$$
Rate = \frac{V_{max} \left(\frac{\prod_{i=1}^{n}S_i}{(K_{S1...Sn})^n}\right) - V_{max, rev} \left(\frac{\prod_{i=1}^{n}P_i}{(K_{P1...Pn})^n}\right)}{Z}
$$

ここで：

  * $$
    V_{max}
    $$

    は前向き反応の最大速度
  * $$
    V_{max, rev}
    $$

    は逆反応の最大速度
  * $$
    S_i
    $$

    , $P_i$, $R_i$ は $i^{th}$ 基質（S）、生成物（P）、または調節因子（R）の濃度
  * $$
    K_{X_1...X_n}
    $$

    は動力学定数
  * $$
    Z
    $$

    は [S]、[P]、および [R] の積を K*S*P_R で割ったすべての項の組み合わせ

# 引数

  * `metabs_and_regulators_kwargs...`: 反応の基質、生成物、触媒部位、調節部位、およびその他のパラメータを指定するキーワード引数。

# 戻り値

  * 一般的なqssa速度方程式を使用して反応の速度を計算する関数
  * 速度方程式で使用される代謝物およびパラメータの名前のタプル

```
