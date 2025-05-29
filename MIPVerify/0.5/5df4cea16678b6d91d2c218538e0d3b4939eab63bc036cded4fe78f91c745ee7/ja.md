```julia
batch_find_untargeted_attack(
    nn,
    dataset,
    target_indices,
    optimizer,
    main_solve_options;
    save_path,
    solve_rerun_option,
    pp,
    norm_order,
    tightening_algorithm,
    tightening_options,
    solve_if_predicted_in_targeted,
    adversarial_example_objective
)

```

指定されたニューラルネットワーク `nn` と `dataset` に対して、`target_indices` で特定されたサンプルのために [`find_adversarial_example`](@ref) を実行し、各サンプルのターゲットラベルを真のラベルの補集合に設定します。

この関数は `save_path` に名前付きのディレクトリを作成し、その名前は以下を要約します。

1. `nn` のネットワーク名、
2. 摂動ファミリー `pp`、
3. `norm_order`

このディレクトリ内には、すべての結果の概要が `summary.csv` に保存され、個々の実行の結果はサブフォルダ `run_results` に保存されます。

この関数は中断してクリーンに再起動できるように設計されており、以前の実行の結果を判断するために `summary.csv` ファイルに依存しています（このファイルを手動で変更すると予期しない動作を引き起こす可能性があります）。

サマリーファイルに特定のターゲットインデックスの結果がすでに含まれている場合、`solve_rerun_option` はこの特定のインデックスに対して [`find_adversarial_example`](@ref) を再実行するかどうかを決定します。

`optimizer` は、MIP問題が構築された後に解決するために使用されるオプティマイザーを指定し、`main_solve_options` はメインソルブのためにオプティマイザーに渡されるオプションを指定します。

# Named Arguments:

  * `save_path`: 結果が保存されるディレクトリ。デフォルトは現在のディレクトリです。
  * `pp, norm_order, tightening_algorithm, tightening_options, solve_if_predicted_in_targeted` は [`find_adversarial_example`](@ref) に渡され、同じデフォルト値を持ちます。詳細についてはその関数のドキュメントを参照してください。
  * `solve_rerun_option::MIPVerify.SolveRerunOption`: オプションは `never`, `always`, `resolve_ambiguous_cases`, `refine_insecure_cases` です。詳細については [`run_on_sample_for_untargeted_attack`](@ref) を参照してください。
