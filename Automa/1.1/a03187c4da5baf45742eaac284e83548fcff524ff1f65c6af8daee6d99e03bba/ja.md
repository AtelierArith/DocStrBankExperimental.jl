```
generate_buffer_validator(name::Symbol, regexp::RE; goto=true; docstring=true)
```

`name`という名前の関数を定義するコードを生成します。この関数は、バイトのシーケンスとして解釈される単一の引数`data`を取ります。関数は、`data`が`Machine`と一致する場合は`nothing`を返し、一致しない場合は最初の無効なバイトのインデックスを返します。マシンが予期しないEOFに達した場合は、`0`を返します。

`goto`が`true`の場合、関数はより速いが複雑な`:goto`コードを使用します。 `docstring`が`true`の場合、生成された関数のために自動的にドキュメント文字列を作成します。

参照: [`generate_io_validator`](@ref)
