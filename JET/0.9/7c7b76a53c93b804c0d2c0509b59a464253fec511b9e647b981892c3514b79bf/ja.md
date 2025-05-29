```
report_file(file::AbstractString; jetconfigs...) -> JETToplevelResult
```

`file`を分析して型レベルのエラーを見つけ、検出された問題を返します。

この関数は、`file`のディレクトリ内で`.JET.toml`構成ファイルを探し、ファイルツリー内で*上向き*に検索して`.JET.toml`が見つかるまで（または見つからないまで）探索します。見つかった場合、ファイルに指定された構成が適用されます。詳細については、[JETの構成ファイル仕様](@ref config-file)を参照してください。

[一般的な構成](@ref)および[エラー分析特有の構成](@ref jetanalysis-config)はキーワード引数として指定でき、指定された場合は`.JET.toml`構成ファイルによって指定された構成よりも優先されます。

!!! tip
    パッケージを分析したいが、その関数を実際に使用するファイルがない場合、[`analyze_from_definitions`オプション](@ref toplevel-config)が役立つかもしれません。これは、JETが宣言されたシグネチャに基づいてメソッドを分析できるようにします。たとえば、JETはこの方法で自分自身を分析できます：

    ```julia-repl
    # JET.jlのルートディレクトリから
    julia> report_file("src/JET.jl";
                       analyze_from_definitions = true)
    ```

    [`report_package`](@ref)も参照してください。


!!! note
    この関数は、デフォルトのログレベルで`toplevel_logger`構成を有効にします。明示的に指定して構成することもできます：

    ```julia
    report_file(args...;
                toplevel_logger = nothing, # トップレベルロガーを抑制
                jetconfigs...) # その他の構成
    ```

    詳細については、[JETのトップレベル分析構成](@ref toplevel-config)を参照してください。

