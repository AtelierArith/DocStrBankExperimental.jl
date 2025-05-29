```
labelyst(dataframe, output_file, paper_format::Vector{String}; <kwargs>)
labelyst(dataframe, output_file, paper_format::String, label_division::Vector{Int64}; <kwargs>)
labelyst(dataframe, output_file, paper_format::Vector{String}, label_division::Vector{Int64}; <kwargs>)
```

`julia DataFrame`を取り込み、QRコードと人間が読めるコードを含むラベルの`.pdf`ファイルを生成します。

### キーワード引数

  * `font_size::String`: ラベル上のすべてのテキストのフォントサイズを設定します。デフォルトは`"12pt"`です。
  * `make_pdf::Bool`: 出力を`.pdf`にするか、生の`.typ`ファイルにするかを定義します。デフォルトは`true`です。

# 例

```julia
    # サイズ90mm X 17mmのラベル、1ページに1つ、"pot_labels.pdf"として保存
    labelyst(dataframe, "pot_labels", ["90mm", "17mm"])

    # DIN A4ページに30ラベル（10行 x 3列）、"adh_labels.pdf"として保存
    labelyst(dataframe, "adh_labels", "a4", [10, 3])

    # カスタムサイズのページに50ラベル（10行 x 5列）、"cust_lab.pdf"として保存
    labelyst(dataframe, "cust_lab", ["178mm", "250mm"], [10, 5]; font_size = "8pt") 
```
