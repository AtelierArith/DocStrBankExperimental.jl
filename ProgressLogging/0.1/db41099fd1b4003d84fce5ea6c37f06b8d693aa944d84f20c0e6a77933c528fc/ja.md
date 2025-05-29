# ProgressLogging: プログレスログを定義するためのパッケージ

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://junolab.github.io/ProgressLogging.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://junolab.github.io/ProgressLogging.jl/dev) [![Build Status](https://travis-ci.com/JunoLab/ProgressLogging.jl.svg?branch=master)](https://travis-ci.com/JunoLab/ProgressLogging.jl) [![Codecov](https://codecov.io/gh/JunoLab/ProgressLogging.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JunoLab/ProgressLogging.jl) [![Coveralls](https://coveralls.io/repos/github/JunoLab/ProgressLogging.jl/badge.svg?branch=master)](https://coveralls.io/github/JunoLab/ProgressLogging.jl?branch=master)

ProgressLogging.jlは*プログレスログ*を定義するためのパッケージです。時間のかかる本体を持つループの進行状況を報告するために使用できます：

```julia
julia> using ProgressLogging

julia> @progress for i in 1:10
           sleep(0.1)
       end
```

このパッケージにはプログラムの進行状況を視覚化するための*プログレスモニター*は含まれていません。ProgressLogging.jl APIによって作成されたプログレスログをサポートするパッケージをインストールする必要があります。例えば：

  * [Juno](https://junolab.org/)
  * [TerminalLoggers.jl](https://github.com/c42f/TerminalLoggers.jl)
