```
tp_flash(model, p, T, n, method::TPFlashMethod = DETPFlash())
```

反応しない多成分フラッシュ問題を解決するためのルーチン。デフォルトのメソッドはグローバル最適化を使用します。 [`DETPFlash`](@ref) を参照してください。

入力:

  * T, 温度
  * p, 圧力
  * n, 各種のモル数のベクトル

出力 - タプルに含まれる:

  * xᵢⱼ, 相 i における種 j のモル分率の配列
  * nᵢⱼ, 相 i における種 j のモル数の配列, [mol]
  * G, 平衡混合物のギブズ自由エネルギー [J]

```
