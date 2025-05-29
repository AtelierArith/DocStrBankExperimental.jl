```julia
System(
    sys_file::AbstractString,
    dyr_file::AbstractString;
    kwargs...
) -> Any

```

PSS/e テキストファイルから静的および動的データを直接解析します。利用可能な動的注入モデルと静的対応物の間のすべての関係を自動的に生成します。

id でインデックス付けされた各辞書は、そのコンポーネントのベクトルを 5 つ含んでいます：

  * 機械
  * シャフト
  * AVR
  * タービン制御
  * PSS

ファイルは .raw ファイル (PTI データ形式) と .dyr ファイルから解析する必要があります。

## 例：

```julia
raw_file = "Example.raw"
dyr_file = "Example.dyr"
sys = System(raw_file, dyr_file)
```
