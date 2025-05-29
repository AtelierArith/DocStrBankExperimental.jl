```
Save(filename="machine.jls")
```

反復制御、例えば、`Save("run3/machine.jls")`のように。

提供された`filename`を使用して、反復中のマシンの現在の状態をディスクに保存します。番号で装飾されており、例えば「run3/machine42.jls」のようになります。デフォルトの動作はSerializationモジュールを使用しますが、`method=save_fn(::String, ::Any)`引数を設定することで変更できます。ここで`save_fn`は任意のシリアル化メソッドです。「反復中のマシン」とは何かについての詳細は、[`IteratedModel`](@ref)を参照してください。
