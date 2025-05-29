```
@texeq_str -> katex_html_code
```

PlutoでレンダリングされたときにKaTeXを使用してlatex方程式を表示するHTML出力を生成するために使用します。

[`texeq`](@ref)に依存していますが、バックスラッシュの二重エスケープの必要を回避します。

# 例

```julia
texeq"
\frac{q \sqrt{2}}{15} + 42
"
```
