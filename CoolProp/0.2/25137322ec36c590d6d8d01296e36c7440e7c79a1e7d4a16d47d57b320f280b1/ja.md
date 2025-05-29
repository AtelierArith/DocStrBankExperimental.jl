```
saturation_ancillary(fluid_name::AbstractString, output::AbstractString, quality::Integer, input::AbstractString, value::Real)
```

飽和補助値から値を抽出します。

# 引数

  * `fluid_name`: 使用する流体の名前 - HelmholtzEOS バックエンドのみ
  * `output`: 希望する出力変数（例えば圧力の場合は "P"）
  * `quality`: 品質、0 または 1
  * `input`: 入力変数 ("T")
  * `value`: 入力値

# 例

julia> saturation_ancillary("R410A","I",1,"T", 300) 0.004877519938463293

# 参照

double saturation*ancillary(const char* fluid*name, const char* output, int Q, const char* input, double value);
