```
params = fit_adsorption_isotherm(df, pressure_col_name, loading_col_name, model)
```

データフレーム `df` を受け取り、吸着等温線データを含み、データに対して解析モデルをフィットさせて最適なパラメータを特定し、辞書として返します。利用可能なモデルは `:henry` と `:langmuir` です。

ヘンリーモデルは次の形を取ります: N = HP 特定されたヘンリー係数は `params["H"]` です。

ラングミュアモデルは次の形を取ります: N = (MKP)/(1+KP) ここで N は総吸着量、M は最大単層被覆、K はラングミュア定数、P は気体の圧力です。

# 引数

  * `df::DataFrame`: 等温線のための圧力と吸着データを含むデータフレーム
  * `pressure_col_name::Symbol`: 圧力列のヘッダー。`names(df)` で見つけることができます
  * `loading_col_name::Symbol`: 吸着/ロード列のヘッダー。`names(df)` で見つけることができます
  * `model::Symbol`: 吸着等温線データにフィットさせるために選択されたモデル

# 戻り値

  * `params::Dict{AbstractString, Float64}`: 各モデルに対応するパラメータとフィットのMSEを含む辞書。 `:langmuir` には "M" と "K" が含まれます。 `:henry` には "H" が含まれます。
