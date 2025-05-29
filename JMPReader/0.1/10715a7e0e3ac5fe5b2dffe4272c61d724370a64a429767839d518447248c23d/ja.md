```
function readjmp(fn::AbstractString; select::Union{Nothing, Vector} = nothing; drop::Union{Nothing, Vector} = nothing)
```

JMPファイルを読み込みます。

含める列と除外する列は、キーワード引数 `select` と `drop` を使用して定義できます。これらは、`Integer`、`OrdinalRange`、`String`、`Symbol`、`Regex` の任意の組み合わせを持つ列を定義するベクターです。

## 例

```
using JMPReader
fn = joinpath(pathof(JMPReader), "..", "..", "test", "example1.jmp")
df = readjmp(fn)
```
