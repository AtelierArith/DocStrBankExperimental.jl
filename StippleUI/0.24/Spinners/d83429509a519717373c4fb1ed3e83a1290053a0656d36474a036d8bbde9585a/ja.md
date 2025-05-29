```
spinner(spinner_type::Union{String,Symbol} = "", args...; kwargs...)
```

`spinner`は、ユーザーに現在進行中のプロセスを示すために使用されます。これは重要なUX機能であり、ユーザーにシステムがサーバーからデータを取得したり、重い計算を行ったりするような長期的な活動のために引き続き作業を行っているという感覚を与えます。

---

### 例

---

### モデル

```julia-repl
julia> @vars SpinnerModel begin
          box::R{String} = "box"
          comment::R{String} = "comment"
          hourglass::R{String} = "hourglass"
       end
```

### ビュー

```julia-repl
julia> spinner(color="primary", size="3em")
julia> spinner(:box, color="orange",size="5.5em")
julia> spinner(:comment, color="green",size="3em")
julia> spinner(:hourglass, color="purple", size="4em")
```

---

### 引数

---

  * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名（xs|sm|md|lg|xl）を含む ex. `16px`  `2rem`  `xs` `md`
  * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名 ex. `primary` `teal`
  * `thickness::Int` - ストローク幅に使用するオーバーライド値 ex. `5`
