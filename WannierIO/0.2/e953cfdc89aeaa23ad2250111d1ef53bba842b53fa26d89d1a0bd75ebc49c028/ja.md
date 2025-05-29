```
read_win(filename; fix_inputs=true)
read_win(filename, ::Wannier90Text; fix_inputs=true)
read_win(filename, ::Wannier90Toml; fix_inputs=true)
```

wannier90 入力 `win` ファイルを読み込みます。

# 引数

  * `filename`: 入力ファイルの名前。

# キーワード引数

  * `fix_inputs`: 入力パラメータの妥当性チェックと修正を行います。例えば、`num_bands` が指定されていない場合は `num_bands = num_wann` に設定し、常に `atoms_cart` を `atoms_frac` に変換します。詳細は [`fix_win!`](@ref) を参照してください。
