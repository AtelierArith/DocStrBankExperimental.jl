# ConsoleProgressMonitor.jl: ProgressMeter.jl-Logging.jl ブリッジ

[![Build Status](https://travis-ci.com/tkf/ConsoleProgressMonitor.jl.svg?branch=master)](https://travis-ci.com/tkf/ConsoleProgressMonitor.jl) [![Codecov](https://codecov.io/gh/tkf/ConsoleProgressMonitor.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/tkf/ConsoleProgressMonitor.jl) [![Coveralls](https://coveralls.io/repos/github/tkf/ConsoleProgressMonitor.jl/badge.svg?branch=master)](https://coveralls.io/github/tkf/ConsoleProgressMonitor.jl?branch=master)

**注意:** [TerminalLoggers.jl](https://github.com/c42f/TerminalLoggers.jl) がこのパッケージを置き換えます。TerminalLoggers.jl を使用してください。

## 使用法

### セットアップ

```julia
julia> using ConsoleProgressMonitor

julia> ConsoleProgressMonitor.install_logger();
```

または、`ConsoleProgressMonitor.with_progresslogger` を使用して、一時的に `ConsoleProgressMonitor` を有効にします。

### プログレスメーターの表示

[`Juno.progress`](http://docs.junolab.org/latest/man/juno_frontend/#Progress-Meters-1) 仕様に互換性のあるすべてのログイベントは、`ProgressMeter.Progress` を使用して表示されます。

```julia
julia> using Logging: @logmsg, LogLevel

julia> let id = gensym(:id)
           for i = 1:10
               sleep(0.1)
               @logmsg LogLevel(-1) "iterating" progress=i/10 _id=id
           end
           @logmsg LogLevel(-1) "iterating" progress="done" _id=id
       end
```
