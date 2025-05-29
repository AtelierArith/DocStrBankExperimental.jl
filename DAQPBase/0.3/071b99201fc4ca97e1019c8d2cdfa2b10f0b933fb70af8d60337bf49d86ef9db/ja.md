# 例の呼び出し

```
xstar, fval, exitflag, info = DAQPBase.quadprog(H,f,A,bupper)
xstar, fval, exitflag, info = DAQPBase.quadprog(H,f,A,bupper,blower,sense)
```

は、二次計画問題の解 `xstar` を見つけます

```
 minimize	   0.5 x' H x + f' x
subject to   blower <= A x <= bupper
```

`bupper` と `blower` が `A` の行数よりも多くの要素を持つ場合、最初の要素は単純な境界として解釈されます。例えば：

```
    A = [7.0 8.0]
    blower = [-4.0; -5.0; -6.0]
    bupper = [ 1.0;  2.0;  3.0]
```

は次のように解釈されます

```
        -4.0 <= x₁ <= 1.0
        -5.0 <= x₂ <= 2.0
    -6.0 <= 7 x₁ + 8 x₂ <= 3.0

```

# 入力

  * `H`           - コスト行列
  * `f`           - コストベクトル
  * `A`           - 線形制約行列
  * `buppe`       - 制約の上限
  * `blower`      - 制約の下限 (デフォルト: -Inf)
  * `sense`       - 制約のタイプ、Cintsのベクトルとして (デフォルト: 0)。例のタイプ：

      * `0` : 不等式
      * `1` : アクティブ不等式 (ウォームスタートとして使用)
      * `5` : 等式
      * `8` : ソフト (必要に応じて違反が許可される)
      * `16` : バイナリ (上限または下限のいずれかが等式で成り立つべき)

# 出力

  * `xstar`       - 解
  * `fval`        - `xstar` の目的関数値。
  * `exitflag`    - ソルバーからのフラグ (>0 成功, <0 失敗)
  * `info`        - ソルバーからのプロファイリング情報を含むタプル。
