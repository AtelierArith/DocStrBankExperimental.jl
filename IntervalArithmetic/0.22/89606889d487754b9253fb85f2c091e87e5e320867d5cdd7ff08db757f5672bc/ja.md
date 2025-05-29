```
setdisplay(format::Symbol; decorations::Bool, ng_flag::Bool, sigdigits::Int)
```

`show` でインターバルを表示するために使用されるフォーマットを変更します。

可能なオプション：

  * `format` は次のいずれかです：

      * `:infsup`: インターバルを `[a, b]` として表示します。
      * `:midpoint`: インターバルを `m ± r` として表示します。
      * `:full`: インターバルの境界を完全に表示し、`sigdigits` を無視します。
  * `decorations`: 装飾を表示するかどうか。
  * `ng_flag`: NG フラグを表示するかどうか。
  * `sigdigits`: 表示する有効数字の数（1以上）。

初期状態では、表示オプションは `setdisplay(:infsup; decorations = true, ng_flag = true, sigdigits = 6)` に設定されています。`format`、`decorations`、`ng_flag`、および `sigdigits` のいずれかが省略された場合、その値は変更されません。

# 例

```jldoctest
julia> setdisplay(:infsup; decorations = true, sigdigits = 6) # デフォルトの表示オプション
表示オプション:
  - format: infsup
  - decorations: true
  - NG flag: true
  - significant digits: 6

julia> x = interval(0.1, 0.3)
[0.0999999, 0.300001]_com

julia> setdisplay(:full)
表示オプション:
  - format: full
  - decorations: true
  - NG flag: true
  - significant digits: 6 (無視される)

julia> x
Interval{Float64}(0.1, 0.3, com)

julia> setdisplay(:infsup; sigdigits = 3)
表示オプション:
  - format: infsup
  - decorations: true
  - NG flag: true
  - significant digits: 3

julia> x
[0.0999, 0.301]_com

julia> setdisplay(; decorations = false)
表示オプション:
  - format: infsup
  - decorations: false
  - NG flag: true
  - significant digits: 3

julia> x
[0.0999, 0.301]
```
