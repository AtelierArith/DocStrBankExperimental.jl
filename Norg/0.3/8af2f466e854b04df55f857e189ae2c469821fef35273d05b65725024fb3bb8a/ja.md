Norg.jlは、純粋なJuliaで[Neorg](https://github.com/nvim-neorg/neorg)ファイルを解析する方法を提供します。

カスタムターゲットで`Base.parse`をオーバーロードします。これまでのところ、利用可能なターゲットは`HTMLTarget`のみです。

使用例：

```julia
using Norg
norg(HTMLTarget(), "Read {https://github.com/nvim-neorg/norg-specs}[the spec !]")
```
