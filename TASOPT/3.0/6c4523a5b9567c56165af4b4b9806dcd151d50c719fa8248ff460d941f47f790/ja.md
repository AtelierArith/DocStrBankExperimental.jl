```
output_csv(ac::TASOPT.aircraft=TASOPT.load_default_model(), 
        filepath::String=joinpath(TASOPT.__TASOPTroot__, "IO/default_output.csv");
        overwrite::Bool = false, indices::Dict = default_output_indices,
        includeMissions::Union{AbstractVector,Colon,Bool,Integer} = false, 
        includeFlightPoints::Union{AbstractVector,Colon,Bool,Integer} = false,
        forceMatrices::Bool = false)
```

は、`ac`の値をCSVファイル`filepath`に書き込み、インデックス変数をヘッダーとして使用します。デフォルトでは、最初の巡航点での設計ミッションの典型的な値のセットが出力されます。ヘッダーが互換性がある場合は既存の`filepath`に追加し、そうでない場合はファイル名に整数のサフィックスを追加します。

出力は以下のようにカスタマイズ可能です：

  * `indices`: 各パラメータ配列の希望するインデックスを指定します。
  * `includeMissions`: すべてのミッションを出力するか（すなわち、=true）、指定可能なインデックスを出力します（例：=[1,2,3]）。
  * `includeFlightPoints`: すべてのフライトポイントを出力するか（`includeMissions`と同様）。

!!! details "🔃 入力と出力"
    **入力:**

      * `ac::TASOPT.aircraft`: 任意の状態のモデルを含むTASOPT航空機`struct`。
      * `filepath::String`: 書き込む.csvファイルのパスと名前。
      * `overwrite::Bool`: trueのときにfilepathにある既存のファイルを削除します。デフォルトはfalseです。
      * `indices::Dict{String => Union{AbstractVector,Colon(), Integer}}`: キーとして与えられたパラメータ配列の希望するインデックスを指定します。カスタマイズ可能で、組み込みオプションは[`default_output_indices`](@ref)、`output_indices_all`、および`output_indices_wEngine`です。
      * `includeMissions::Union{AbstractVector,Colon,Bool,Integer}`: trueのときにすべてのミッションエントリをCSVセル内の配列として保存します。デフォルトはfalseで、フライトポイントも出力される場合は内部のネストされた配列になります。特定のインデックスも整数のベクトルとして指定できます。
      * `includeFlightPoints::Union{AbstractVector,Colon,Bool,Integer}`: trueのときにすべてのフライトポイントエントリをCSVセル内の配列として保存します。デフォルトはfalseで、ミッションも出力される場合は外部のネストされた配列になります。特定のインデックスも整数のベクトルとして指定できます。
      * `forceMatrices::Bool`: ミッションとフライトポイントに応じて変化するすべてのエントリがネストされた配列構造に従うように強制します。
      * `struct_excludes::AbstractVector{String}`: ac構造体の出力から除外するフィールドの名前/部分文字列。デフォルトは`[]`で、何も除外しません。

    **出力:**

      * `newfilepath::String`: 実際の出力ファイルパス。ヘッダーの競合がある場合は更新されます。`overwrite = true`の場合は入力ファイルパスと同じです。

