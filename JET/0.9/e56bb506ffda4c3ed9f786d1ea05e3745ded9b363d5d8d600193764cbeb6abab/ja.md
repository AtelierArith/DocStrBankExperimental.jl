```
watch_file(file::AbstractString; jetconfigs...)
```

`file`を監視し、コードの更新時に[`report_file`](@ref)で分析を再トリガーします。JETは`file`から到達可能なすべての`include`されたファイルを分析しようとし、`include`されたファイルのいずれかでコードの更新が検出された場合に分析を再トリガーします。

このエントリーポイントは現在、[Revise.jl](https://timholy.github.io/Revise.jl/stable/)を使用してコードの更新を監視しており、*Reviseがセッションにロードされた後にのみ使用できます*。したがって、使用するには、例えば、以前の段階で`using Revise`を実行しておく必要があります。Reviseは、`revise_modules = [Base]`のような設定を使用してJETによって直接分析されないファイルの変更を追跡する可能性を提供します。詳細については、[watch configurations](@ref watch-config)を参照してください。

!!! warning
    このインターフェースは非常に実験的であり、通知なしに変更または削除される可能性があります。


他にも[`report_file`](@ref)を参照してください。
