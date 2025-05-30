```
code_inferred(@nospecialize(f), t::Type...; 
        world = Base.get_world_counter(),
        interp = Core.Compiler.NativeInterpreter(world))
```

`Core.MethodInstance` 特化のシグネチャ `Tuple{typeof(f), t::Type...}` に対する特化を導出し、`interp` で推論します。これは、カスタムコンパイルパイプラインの一部として、またはデバッグ目的で、推論された低レベルコードを導出するために使用できます。

`code_inferred` には、ユーザーが特化に関連付けられたキャッシュされた `Core.CodeInfo` に対して推論を不注意に複数回実行するのを防ぐ明示的なチェックが含まれています。

!!! warning
    推論と最適化は状態を持つ – 推論された `Core.CodeInfo` を取得して消去し、[`lambda`](@ref) を通して押し込むような「愚かな」ことを試みると、うまくいかない可能性が非常に高く、あなたの顔に爆発する可能性が非常に高いです。

    推論はまた、`Core.MethodInstance` 特化に関連付けられた推論された `Core.CodeInfo` を *インタープリターに関係なく* キャッシュします。つまり（私がこの時点で知っている限り）、推論実行の間にキャッシュの無効化を強制しない限り、複数のインタープリターで迅速に推論することはできません。

