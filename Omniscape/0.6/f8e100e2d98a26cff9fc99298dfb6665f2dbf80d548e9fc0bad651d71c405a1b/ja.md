INIメソッド:

```
run_omniscape(path::String)
```

メモリ内メソッド:

```
run_omniscape(
    cfg::Dict{String, String}
    resistance::MissingArray{Number, 2};
    reclass_table = MissingArray{Float64, 2}(undef, 1, 2),
    source_strength = source_from_resistance(resistance, cfg, reclass_table),
    condition1 = MissingArray{Float64, 2}(undef, 1, 1),
    condition2 = MissingArray{Float64, 2}(undef, 1, 1),
    condition1_future = MissingArray{Float64, 2}(undef, 1, 1),
    condition2_future = MissingArray{Float64, 2}(undef, 1, 1),
    wkt = "",
    geotransform = [0.0, 1.0, 0.0, 0.0, 0.0, -1.0],
    write_outputs = false
)
```

全方向の電流フローを計算します。メモリ内メソッドのすべての配列入力は `MissingArray{T, 2}` 型である必要があります。これは `Array{Union{Missing, T}, 2}` のエイリアスです。`missing` エントリは NoData ピクセルに対応します。数値の NoData 値を持つ配列から始める場合は、[`missingarray`](@ref) を使用して `MissingArray` に変換してください。

# パラメータ

**`path`**: 実行パラメータを含む INI ファイルへのパス。実行パラメータの説明については、ユーザーガイドの [設定とオプション](@ref) セクションを参照してください。

**`cfg`**: Omniscape 実行パラメータの辞書。実行パラメータとそのデフォルト値の説明については、ユーザーガイドの [設定とオプション](@ref) セクションを参照してください。`run_omniscape` のメモリ内メソッドは、次のキーを無視します: `resistance_file`, `source_file`, `reclass_table`, `condition1_file`, `condition2_file`, `condition1_future_file`, および `condition2_future_file`。これらはすべてファイルパスを指定するため、`run_omniscape` のメモリ内メソッドには適用されません。

**`resistance`**: 抵抗値の 2D、北向き配列。NoData（無限の抵抗）には `missing` を使用します。`resistance` にはゼロまたは負の値を含めることはできません。

# キーワード引数

**`reclass_table`**: 2 列の配列。最初の列には抵抗面の元の抵抗値が含まれ、2 番目の列にはそれらの値が変更されるべき内容が指定されます。値を `missing` に再分類して無限の抵抗（NoData）に置き換えることができます。

**`source_strength`**: 抵抗と同じサイズの 2D、北向き配列のソース強度値。`cfg` の `source_from_resistance` が "false"（デフォルト値）に設定されている場合にのみ必要です。

**`condition1`**: オプション。`cfg` の `conditional` が "true" に設定されている場合に必要です。抵抗と同じサイズの 2D、北向き配列。詳細については [気候接続性](@ref) および [条件付き接続性オプション](@ref) を参照してください。

**`condition2`**: オプション。`cfg` の `conditional` が "true" に設定され、`n_conditions` が "2" に設定されている場合に必要です。抵抗と同じサイズの 2D、北向き配列。詳細については [気候接続性](@ref) および [条件付き接続性オプション](@ref) を参照してください。

**`condition1_future`**: オプション。`cfg` の `conditional` が "true" に設定され、`compare_to_future` が "1" または "both" に設定されている場合に必要です。抵抗と同じサイズの 2D、北向き配列。詳細については [気候接続性](@ref) および [条件付き接続性オプション](@ref) を参照してください。

**`condition2_future`**: オプション。抵抗と同じサイズの 2D、北向き配列。詳細については [気候接続性](@ref) および [条件付き接続性オプション](@ref) を参照してください。`cfg` の `conditional` が "true" に設定され、`n_conditions` が "2" に設定され、`compare_to_future` が "2" または "both" に設定されている場合に必要です。

**`wkt`**: 空間データ入力に使用される投影の Well Known Text 表現をオプションで指定します。Omniscape がラスタ出力をディスクに書き込む場合にのみ使用されます。

**`geotransform`**: `wkt` に加えて、オプションでジオトランスフォームを指定します。ジオトランスフォームは、北向きの画像に対して次の要素を持つ 6 要素のベクトルです: `[<左上隅の x 座標>, <ピクセル幅>, <行の回転（通常は 0）>, <左上隅の y 座標>, <列の回転（通常は 0）>, <ピクセル高さ（負の数）>]`。ラスタ出力をディスクに書き込むときにのみ使用されます。

**`write_outputs`**: 出力をディスクに書き込むかどうかを指定するブール値。デフォルトは `false` です。`true` の場合、`cfg` は `project_name` キーの値を含む必要があります。
