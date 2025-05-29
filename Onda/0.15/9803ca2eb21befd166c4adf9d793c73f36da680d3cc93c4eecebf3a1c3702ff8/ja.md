```
encode(sample_type::DataType, sample_resolution_in_unit, sample_offset_in_unit,
       sample_data, dither_storage=nothing)
```

`sample_data`を`sample_type`、`sample_resolution_in_unit`、および`sample_offset_in_unit`に従って量子化したコピーを返します。`sample_type`は`Onda.LPCM_SAMPLE_TYPE_UNION`の具体的なサブタイプでなければなりません。個々のサンプル`s`の量子化は次のように行われます：

```
round(S, (s - sample_offset_in_unit) / sample_resolution_in_unit)
```

エンコーディングのダイナミックレンジを超える値をクリップするための追加の特別な処理があります。

`dither_storage isa Nothing`の場合、量子化の前にディザリングは適用されません。

`dither_storage isa Missing`の場合、ディザストレージが自動的に割り当てられ、量子化の前に三角形ディザリングが情報に適用されます。

それ以外の場合、`dither_storage`は`sample_data`と同様の形状と型のコンテナでなければなりません。このコンテナは、量子化の前に情報に適用される三角形ディザリングプロセスに必要なランダムノイズを格納するために使用されます。

もし：

```
sample_type === eltype(sample_data) &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

であれば、この関数は単に`sample_data`をコピー/ディザリングせずに直接返します。
