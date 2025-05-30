```
hex(c::Colorant)
hex(c::Colorant, style::Symbol)
```

色を16進数の文字列に変換します。スタイルを指定することもできます。

# 引数

  * `c`: 対象の色。
  * `style`: 16進数表記を指定するためのシンボル。大文字のシンボルを指定すると、返される値は大文字になります。以下のシンボルが利用可能です：

      * `:AUTO`: `c`のタイプに応じて自動的に選択される表記
      * `:RRGGBB`/`:rrggbb`: 6桁の不透明表記
      * `:AARRGGBB`/`:aarrggbb`: アルファが先頭にある8桁の表記
      * `:RRGGBBAA`/`:rrggbbaa`: アルファが末尾にある8桁の表記
      * `:RGB`/`:rgb`/`:ARGB`/`:argb`/`:RGBA`/`:rgba`: 3桁または4桁の表記
      * `:S`/`:s`: 利用可能な場合の短い表記

# 例

```jldoctest; setup = :(using Colors)
julia> hex(RGB(1,0.5,0))
"FF8000"

julia> hex(ARGB(1,0.5,0,0.25))
"40FF8000"

julia> hex(HSV(30,1.0,1.0), :AARRGGBB)
"FFFF8000"

julia> hex(ARGB(1,0.533,0,0.267), :rrggbbaa)
"ff880044"

julia> hex(ARGB(1,0.533,0,0.267), :rgba)
"f804"

julia> hex(ARGB(1,0.533,0,0.267), :S)
"4F80"
```

!!! compat "Colors v0.12"
    `style` は少なくとも Colors v0.12 が必要です。

