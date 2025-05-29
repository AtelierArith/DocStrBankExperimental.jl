出力 `Y` と入力 `U` をフィードバックループで関連付ける閉ループ伝達関数。

得られた閉ループ伝達関数は次のとおりです：

```
 Y      top
--- = --------
 U    1 + g_ol
```

# 例

```jldoctest
g_ol = 4 / (s + 1) * 2 / (s + 2)
top = 5 / (s + 4)
g = ClosedLoopTransferFunction(top, g_ol)
# 出力
閉ループ伝達関数。
      top
    -------
    1 + g_ol

  top =
    5.0
-----------
1.0*s + 4.0

  g_ol =
         8.0
---------------------
1.0*s^2 + 3.0*s + 2.0
```

# 属性

  * `top::TransferFunction`: 分子
  * `g_ol::TransferFunction`: 開ループ伝達関数
