```
@unithydro name begin ... end
```

`UnitHydrograph`オブジェクトの構築を簡素化するマクロです。

# 使用法

```julia
@unithydro :my_uh begin
    uh_func = begin
        # ピースワイズUH関数を定義: max_time => 式
        lag => 0.5 * (t / lag)^2.5
        2lag => 1.0 - 0.5 * abs(2 - t / lag)^2.5
    end
    uh_vars = [runoff] # 入力変数
    configs = (solvetype=:SPARSE, suffix=:_routed)
end
```

指定された名前、ピースワイズUH関数定義（`uh_func`）、入力変数（`uh_vars`）、および構成（`configs`）を持つ`UnitHydrograph`を`begin...end`ブロック内で定義します。

# 引数

  * `name`: （オプション）ユニットハイドログラフ名のシンボル。
  * `block`: `uh_func`、`uh_vars`、およびオプションで`configs`の代入を含む`begin...end`ブロック。

# 戻り値

  * `UnitHydrograph`インスタンス。
