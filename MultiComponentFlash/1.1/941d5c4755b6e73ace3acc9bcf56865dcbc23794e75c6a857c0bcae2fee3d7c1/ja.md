```
flash_2ph(eos, c, [K], [V]; <キーワード引数>)
```

与えられたEOSの下で特定の条件のセットに基づいて二相フラッシュを実行します。蒸気分率を返します。Kをインプレースで修正します。

圧力、温度、モル分率を持つ混合物が与えられた場合、このルーチンは安定性テストの後に蒸気-液体平衡計算を実行します。

2つの結果が可能です：

1. 単相条件が支配する（返される蒸気分率は`NaN`）場合、単相（液体または蒸気）が安定しています。
2. 二相条件が可能です。このルーチンはK値と蒸気分率を生成し、次の条件が成り立つようにします：

    1. すべての成分に対する等フガシティ制約（$f_{li} = f_{vi}$）
    2. すべての成分に対するモルバランス（$(1-V) x_i - V y_i - z_i$）
    3. 単位条件（$\sum_i (x_i - y_i) = 0$）

# 引数

  * `eos`: フラッシュに使用する状態方程式
  * `c`: 混合物をフラッシュする条件の形式 `(p = 10e5, T = 303.15, z = [0.5, 0.3, 0.2])`
  * `K`: オプションで、K値を保持するために使用される長さ `number_of_components(eos)` のバッファ。インプレースで修正されます。
  * `V`: オプションで、Vの初期推定値。もしこの値が`NaN`でない場合、安定性チェックはスキップされます。

# キーワード引数

  * `method = SSIFlash()`: 使用するフラッシュメソッド。`SSIFlash()`, `NewtonFlash()`または`SSINewtonFlash()`のいずれか。
  * `tolerance = 1e-8`: 収束基準のための許容誤差。$\|1-R_i\|_\infty$に対して相対的であり、$R_i = f_{il}/f_{iv}$
  * `maxiter = 20000`: 安定性テストとメインフラッシュの両方の最大反復回数。
  * `verbose = false`: 解決中に追加情報を出力します。
  * `extra_out = false`: `V`だけでなく、`conv`に反復回数と収束状態を含む`(V, K, conv)`を返します。
  * `check = true`: 警告（収束していない場合）とエラー（フラッシュが失敗した場合）を出力します。
  * `z_min`: 最小組成（提供された場合は強制されます）

参照：[`flash_2ph!`](@ref), [`single_phase_label`](@ref)
