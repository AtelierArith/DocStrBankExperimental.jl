```
tinf = @snoop_inference commands;
```

juliaの型推論のプロファイルを生成し、`commands`を実行中に処理された各`MethodInstance`の推論に費やされた時間を記録します。型推論への新しいエントリ（`commands`内で直接実行された場合でも、ランタイムディスパッチによって呼び出された場合でも）も、呼び出し元を特定できるようにバックトレースを収集します。

`tinf`はツリーであり、各ノードは特定の推論「フレーム」に関するデータ（メソッド、引数型の特化、パラメータ、さらには定数伝播された値など）を含んでいます。各ノードは[`exclusive`](@ref)/[`inclusive`](@ref)時間を報告し、exclusive時間はこのフレーム自体の推論に費やされた時間に対応し、inclusive時間はこのフレームのすべての呼び出し先を推論するのに必要な時間を含みます。

このプロファイルツリーの最上位ノードは`ROOT`です。ユニークに、exclusive時間はjuliaの型推論*以外*に費やされた時間に対応します（コード生成、llvm_opt、ランタイムなど）。

`tinf`を効果的に操作するには、`SnoopCompile`をロードする必要があります。

!!! warning
    `@snoop_inference`マクロ呼び出しの末尾にセミコロン`;`があることに注意してください。`SnoopCompileCore`はコードを無効にすることが許可されていないため、`tinf`をきれいに表示する`Base.show`メソッドを定義することができません。`SnoopCompile`がロードされるまで`tinf`の検査を延期してください。


# 例

```jldoctest; setup=:(using SnoopCompileCore), filter=r"([0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?/[0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?|\d direct)"
julia> tinf = @snoop_inference begin
           sort(rand(100))  # コードを評価し、juliaの型推論をプロファイルします
       end;
```
