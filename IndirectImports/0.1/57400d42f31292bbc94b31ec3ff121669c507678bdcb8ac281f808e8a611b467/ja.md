# IndirectImports

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://tkf.github.io/IndirectImports.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://tkf.github.io/IndirectImports.jl/dev) ![GitHub commits since tagged version](https://img.shields.io/github/commits-since/tkf/IndirectImports.jl/v0.1.1.svg) [![Build Status](https://travis-ci.com/tkf/IndirectImports.jl.svg?branch=master)](https://travis-ci.com/tkf/IndirectImports.jl) [![Codecov](https://codecov.io/gh/tkf/IndirectImports.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/tkf/IndirectImports.jl) [![Coveralls](https://coveralls.io/repos/github/tkf/IndirectImports.jl/badge.svg?branch=master)](https://coveralls.io/github/tkf/IndirectImports.jl?branch=master)

IndirectImports.jlは、Juliaパッケージがそれらを定義するパッケージをインポートせずに（特別なタイプの）関数を呼び出し、拡張することを可能にします。これはオプションの依存関係を管理するのに便利です。

  * Requires.jlと比較して、IndirectImports.jlのアプローチはより静的で、ランタイムの`eval`がないため、コンパイラに優しいです。しかし、Requires.jlとは異なり、上流および下流のパッケージは両方ともIndirectImports.jl APIに依存する必要があります。
  * "XBase.jl"アプローチと比較して、IndirectImports.jlは、追加のパッケージを作成し、それを"実装"パッケージと同期させる必要がないという点で、より柔軟です。しかし、"XBase.jl"アプローチとは異なり、IndirectImports.jlは関数にのみ使用可能で、型には使用できません。

## 例

```julia
# MyPlot/src/MyPlot.jl
module MyPlot
    using IndirectImports

    @indirect function plot end  # "間接関数"を宣言

    @indirect function plot(x)  # オプション
        # 一般的な実装
    end
end

# MyDataFrames/src/MyDataFrames.jl
module MyDataFrames
    using IndirectImports

    @indirect import MyPlot  # これは実際にはMyPlot.jlをロードしません

    # 間接関数を拡張できます
    @indirect function MyPlot.plot(df::MyDataFrame)
        # 間接関数を呼び出すことができます
        MyPlot.plot(df.columns)
    end
end
```

`]add IndirectImports`でインストールできます。詳細は[ドキュメント](https://tkf.github.io/IndirectImports.jl/dev/)を参照してください。
