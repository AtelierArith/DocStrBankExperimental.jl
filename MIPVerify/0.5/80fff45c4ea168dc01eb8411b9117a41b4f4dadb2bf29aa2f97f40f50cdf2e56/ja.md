```julia
find_adversarial_example(
    nn,
    input,
    target_selection,
    optimizer,
    main_solve_options;
    invert_target_selection,
    pp,
    norm_order,
    adversarial_example_objective,
    tightening_algorithm,
    tightening_options,
    solve_if_predicted_in_targeted
)

```

`input`を摂動させて、ネットワーク`nn`が摂動した画像を`target_selection`のインデックスで特定されたカテゴリの1つに分類するようにします。

重要:

1. `target_selection`には`input`の正しいラベルが含まれる場合があります。
2. （特に`closest`目的の場合）「引き分け」を見ることが可能です。つまり、摂動した入力が2つのロジット（1つはターゲットカテゴリに対応し、もう1つは非ターゲットカテゴリに対応）を同じ最大値で出力することがあります。以下の正式な定義を参照してください。特に「≥」記号に注意してください。

`optimizer`はMIP問題を構築し、解決するために使用されます。

出力辞書には、`：Model`、`：PerturbationFamily`、`：TargetIndexes`、`：SolveStatus`、`：Perturbation`、`：PerturbedInput`、`：Output`というキーがあります。個々の辞書エントリが何に対応するかについては、[チュートリアル](https://nbviewer.jupyter.org/github/vtjeng/MIPVerify.jl/blob/master/examples/03_interpreting_the_output_of_find_adversarial_example.ipynb)を参照してください。

*正式な定義*: 合計`n`カテゴリがある場合、（摂動された）出力ベクトル`y=d[:Output]=d[:PerturbedInput] |> nn`の長さは`n`です。`:SolveStatus`が実現可能であれば、`y[j] - y[i] ≥ 0`がある`j ∈ target_selection`に対して、すべての`i ∉ target_selection`に対して保証されます。

# キーワード引数:

  * `invert_target_selection`: デフォルトは`false`です。`true`の場合、`target_selection`をその補集合に設定します。
  * `pp`: デフォルトは`UnrestrictedPerturbationFamily()`です。敵対的例の探索空間を決定します。
  * `norm_order`: デフォルトは`1`です。摂動した画像と元の画像との距離を決定するために使用される距離ノルムを決定します。許可されるオプションは`1`と`Inf`、および`optimizer`がMIQPを解決できる場合は`2`です。
  * `adversarial_example_objective`: デフォルトは`closest`です。許可されるオプションは`closest`または`worst`です。

      * `closest`は、`norm_order`ノルムによって測定された最も近い敵対的例を見つけます。
      * `worst`は、`target_selection`に対する`max(y[j)`と`target_selection`に含まれないすべての`i`に対する`max(y[i])`の間の*最大*ギャップを持つ敵対的例を見つけます。
  * `tightening_algorithm`: デフォルトは`mip`です。各非線形ユニットへの入力の上限と下限を決定する方法を決定します。許可されるオプションは`interval_arithmetic`、`lp`、`mip`です。

      * `interval_arithmetic`は、前の層への出力の境界を見ます。
      * `lp`は、整数制約が緩和された`mip`定式化に対応する`lp`を解決します。
      * `mip`は、完全な`mip`定式化を解決します。
  * `tightening_options`: 非線形ユニットへの入力の上限と下限を決定するために使用されるときに、最適化プログラムに渡されるソルバー固有のオプションです。`tightening_algorithm`が`lp`または`mip`の場合にのみ使用されることに注意してください（境界を計算するために`interval_arithmetic`が使用される場合はソルバーは使用されません）。GurobiおよびHiGHSのデフォルトは、解決ごとに20秒の時間制限で、出力は抑制されます。
  * `solve_if_predicted_in_targeted`: デフォルトは`true`です。摂動されていない`input`に対して`nn`が行う予測は効率的に決定できます。予測されたインデックスが`target_selection`のインデックスの1つである場合、すでに「敵対的例」があるため、MIP問題のモデルを構築する比較的コストのかかるプロセスをスキップできます。すなわち、入力自体です。`solve_if_predicted_in_targeted`が`true`の場合に限り、モデルを構築し、（自明な）MIP問題を解決し続けます。
