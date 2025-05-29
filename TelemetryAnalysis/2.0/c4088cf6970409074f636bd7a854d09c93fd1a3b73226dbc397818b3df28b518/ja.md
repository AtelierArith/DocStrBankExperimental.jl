```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}}]; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DateFrame
```

テレメトリーパケット `tmpackets` を `database` を使用して処理し、**すべての** 登録されたテレメトリの処理された値を返します。`tmpackets` が渡されない場合、デフォルトのテレメトリーパケットが使用されます。

```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}},] telemetries::AbstractVector; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DataFrame
```

テレメトリーパケット `tmpackets` を `database` を使用して処理します。`telemetries` の要素は、テレメトリラベルを持つ `Symbol` または `Pair{Symbol, Symbol}` であることができます。前者の場合、デフォルトのビューが使用されます。後者の場合、変数ビューはペアの2番目のシンボルによって指定された通りになります。詳細については、以下のセクションを参照してください。

`tmpackets` が渡されない場合、デフォルトのテレメトリーパケットが使用されます。

```
process_telemetry_packets([tmpackets::Vector{TelemetryPacket{T}},] telemetries::Vector{Pair{Symbol, Symbol}}; database::TelemetryDatabase, kwargs...) where T <: TelemetrySource -> DataFrame
```

テレメトリーパケット `tmpackets` を `database` を使用して処理します。出力変数は `telemetries` で示されます。これは、テレメトリとその値が出力にどのように書き込まれるかを示すペアのベクトルでなければなりません。例えば、 `:C001 => :raw` はテレメトリ `C001` の生の値を追加し、 `:C001 => :processed` は同じ変数の処理された値を追加します。

出力形式として受け入れられる値は次のとおりです：

  * `:byte_array`: テレメトリバイト配列を持つ `Vector{UInt8}`。
  * `:byte_array_bin`: 生の値がバイナリで表現された文字列。
  * `:byte_array_hex`: 生の値が16進数で表現された文字列。
  * `:processed`: 転送関数から得られた処理された値。
  * `:raw`: テレメトリの生の値。

`tmpackets` が渡されない場合、デフォルトのテレメトリーパケットが使用されます。

!!! info
    キーワード引数 `database` が渡されない場合、デフォルトのデータベースが使用されます。


# キーワード

  * `show_progress::Bool`: `true` の場合、テレメトリを処理している間に進行状況バーが表示されます。 (**デフォルト** = `true`)

# 戻り値

  * `DataFrame`: 選択された値の列を持つ `DataFrame`。列名は変数ラベルです。
