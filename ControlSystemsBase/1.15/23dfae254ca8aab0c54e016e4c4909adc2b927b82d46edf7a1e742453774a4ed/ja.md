```
sysd = c2d(sys::AbstractStateSpace{<:Continuous}, Ts, method=:zoh; w_prewarp=0)
Gd = c2d(G::TransferFunction{<:Continuous}, Ts, method=:zoh)
```

連続時間システム `sys` をサンプル時間 `Ts` を用いて離散時間システムに変換します。指定された `method` (:`zoh`, `:foh`, `:fwdeuler` または `:tustin`) を使用します。

`method = :tustin` は、前ワープ周波数 `w_prewarp` を用いた双線形変換を実行します。

  * `w_prewarp`: Tustin メソッドを使用する際の前ワープ周波数 (rad/s) は、他のメソッドには影響しません。

`c2d_x0map` も参照してください。

# 拡張ヘルプ

ZoH サンプリングは、区分定数入力を持つ線形システムに対して正確です (ステップ不変)。すなわち、[`lsim`](@ref) を使用して得られる解は近似的ではありません (マシン精度のモジュール)。ZoH サンプリングは、離散時間コントローラを使用して制御される連続時間プラントモデルを離散化するために一般的に使用されます。

FoH サンプリングは、区分線形入力を持つ線形システムに対して正確です (ランプ不変)。これは、滑らかな連続入力を持つシステムのシミュレーションに適した選択です。

周波数領域で連続時間システムの挙動をよく近似するためには、`:tustin` (台形 / 双線形) メソッドが最も適切である可能性があります。この場合、前ワープ引数を使用して、離散時間システムの周波数応答が特定の周波数で連続時間システムと一致するようにすることができます。Tustin 変換は状態成分の意味を変更しますが、ZoH および FoH は状態成分の意味を保持します。Tustin メソッドは、連続時間コントローラを離散化するために一般的に使用されます。

前方オイラー法は、一般的にサンプル時間がシステムの時間定数に対して非常に小さい必要があり、その使用は一般的に推奨されません。

制御設計のためのサンプル時間を選択するための古典的な経験則は、`Ts` は $0.2 ≤ ωgc⋅Ts ≤ 0.6$ と選択されるべきであると示しています。ここで $ωgc$ はゲイン交差周波数 (rad/s) です。
