```
energy_preserving_order(rk::RungeKuttaMethod, max_order)
```

この関数は、ハミルトン問題に対して、ルンゲ・クッタ法 `rk` がエネルギー保存的であるのはどの順までかをチェックします。これは、メソッドがエネルギー保存的である順が大きすぎるか無限大の場合に無限に実行されないように、`max_order` を必要とします。

関連情報として [`is_energy_preserving`](@ref) を参照してください。
