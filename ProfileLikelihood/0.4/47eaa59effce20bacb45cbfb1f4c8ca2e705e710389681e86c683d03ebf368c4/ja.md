```
plot_profiles(prof::ProfileLikelihoodSolution, vars = profiled_parameters(prof); 
    ncol=nothing, 
    nrow=nothing,
    true_vals=Dict(vars .=> nothing), 
    spline=true, 
    show_mles=true, 
    shade_ci=true, 
    fig_kwargs=nothing, 
    axis_kwargs=nothing,
    show_points=false,
    markersize=9,
    latex_names=default_latex_names(prof, vars),
    xlim_tuples=nothing,
    ylim_tuples=nothing)
```

プロファイル尤度ソリューション `prof` から結果をプロットします。この関数を使用するには、`using CairoMakie`（または他のMakieバックエンド）を実行している必要があります。

# 引数

  * `prof::ProfileLikelihoodSolution`: [`profile`](@ref) からのプロファイル尤度ソリューション。
  * `vars = profiled_parameters(prof)`: プロットするパラメータ。

# キーワード引数

  * `ncol=nothing`: 使用する列の数。`nothing` の場合、`choose_grid_layout` によって自動的に選択されます。
  * `nrow=nothing`: 使用する行の数。`nothing` の場合、`choose_grid_layout` によって自動的に選択されます。
  * `true_vals=Dict(vars .=> nothing)`: パラメータインデックスをその真の値にマッピングする辞書。存在する場合。`nothing` の場合、何もプロットされず、そうでない場合はプロファイルの真の値に黒い線がプロットされます。
  * `spline=true`: プロットされる曲線が結果を通るスプラインから来るべきか、データ自体をプロットすべきか。
  * `show_mles=true`: MLEの位置に赤い線を置くかどうか。
  * `shade_ci=true`: 信頼区間の間のプロファイルの下の領域をシェードするかどうか。
  * `fig_kwargs=nothing`: `Figure` のための追加のキーワード引数（Makieのドキュメントを参照）。
  * `axis_kwargs=nothing`: `Axis` のための追加のキーワード引数（Makieのドキュメントを参照）。
  * `show_points=false`: プロファイルデータを表示するかどうか。
  * `markersize=9`: `show_points` のために使用されるマーカーサイズ。
  * `latex_names=default_latex_names(prof, vars)`: パラメータに使用するLaTeX名。デフォルトは `syms` 名です。（より特殊な名前の生成されたLaTeXに問題があるかもしれません。必要に応じて問題を作成してください。）
  * `xlim_tuples=nothing`: 各プロットに使用する `xlims`。`nothing` の場合、`xlims` は自動的に設定されます。
  * `ylim_tuples=nothing`: 各プロットに使用する `ylims`。`nothing` の場合、`ylims` は自動的に設定されます。

# 出力

`Figure()` が返されます。

---

```
plot_profiles(prof::BivariateProfileLikelihoodSolution, vars = profiled_parameters(prof); 
    ncol=nothing,
    nrow=nothing,
    true_vals=Dict(1:number_of_parameters(get_likelihood_problem(prof)) .=> nothing),
    show_mles=true,
    fig_kwargs=nothing,
    axis_kwargs=nothing,
    interpolation=false,
    smooth_confidence_boundary=false,
    close_contour=true,
    latex_names=default_latex_names(prof, vars),
    xlim_tuples=nothing,
    ylim_tuples=nothing)
```

二変量プロファイル尤度ソリューション `prof` から結果をプロットします。この関数を使用するには、`using CairoMakie`（または他のMakieバックエンド）を実行している必要があります。

# 引数

  * `prof::ProfileLikelihoodSolution`: [`profile`](@ref) からのプロファイル尤度ソリューション。
  * `vars = profiled_parameters(prof)`: プロットするパラメータ。

# キーワード引数

  * `ncol=nothing`: 使用する列の数。`nothing` の場合、`choose_grid_layout` によって自動的に選択されます。
  * `nrow=nothing`: 使用する行の数。`nothing` の場合、`choose_grid_layout` によって自動的に選択されます。
  * `true_vals=Dict(1:number_of_parameters(get_likelihood_problem(prof)) .=> nothing)`: パラメータインデックスをその真の値にマッピングする辞書。存在する場合。`nothing` の場合、何もプロットされず、そうでない場合は二変量プロファイルのプロットに真の値に黒い点がプロットされます。
  * `show_mles=true`: MLEの位置に赤い点を置くかどうか。
  * `fig_kwargs=nothing`: `Figure` のための追加のキーワード引数（Makieのドキュメントを参照）。
  * `axis_kwargs=nothing`: `Axis` のための追加のキーワード引数（Makieのドキュメントを参照）。
  * `interpolation=false`: プロファイルを補間関数を使用してプロットするか（`true`）、`prof` からのデータを直接使用するか（`false`）。
  * `smooth_confidence_boundary=false`: プロット時に信頼領域の境界をスムーズにするか（`true`）しないか（`false`）。スムージングはスプラインで行われます。
  * `close_contour=true`: 信頼領域の境界の最後の部分を始まりに接続するか（`true`）しないか（`false`）。
  * `latex_names=default_latex_names(prof, vars)`: パラメータに使用するLaTeX名。デフォルトは `syms` 名です。（より特殊な名前の生成されたLaTeXに問題があるかもしれません。必要に応じて問題を作成してください。）
  * `xlim_tuples=nothing`: 各プロットに使用する `xlims`。`nothing` の場合、`xlims` は自動的に設定されます。
  * `ylim_tuples=nothing`: 各プロットに使用する `ylims`。`nothing` の場合、`ylims` は自動的に設定されます。

# 出力

`Figure()` が返されます。
