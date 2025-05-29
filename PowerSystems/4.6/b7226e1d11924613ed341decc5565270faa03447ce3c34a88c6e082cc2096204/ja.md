```julia
TamuSystem(tamu_folder::AbstractString; kwargs...) -> Any

```

PSS/e .RAW (v33) 負荷フローケースからシステムを作成し、関連するMW負荷時系列データを含む.csvを作成します。フォーマットは[テキサスA&M大学テストケースアーカイブ](https://electricgrids.engr.tamu.edu/electric-grid-test-cases/)によって確立されています。

データの一般的なフォーマットはフォルダ:    [casename].raw    [casename]*load*time*series*MW.csv

# 引数

  * `directory::AbstractString`: RAWおよびCSVファイルを含むディレクトリ

# 例

```julia
sys = TamuSystem(
    "./ACTIVSg25k",
    config_path = "ACTIVSg25k_validation.json",
    bus_name_formatter = x->string(x["name"]*"-"*string(x["index"])),
    load_name_formatter = x->strip(join(x["source_id"], "_"))
)
```
