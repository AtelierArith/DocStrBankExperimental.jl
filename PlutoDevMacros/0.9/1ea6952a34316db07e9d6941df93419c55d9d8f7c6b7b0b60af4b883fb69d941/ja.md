```
@addmethod func(args...;kwargs...) = body
@addmethod function func(args...;kwargs...) 
	body
end
```

このシンプルなマクロは、関数定義式を修正します（Plutoノートブックから呼び出されたときのみ）。関数を定義しているモジュールの名前（ここでは `DefiningModule` と呼ばれています）をメソッド定義の前に追加します。

したがって、次のコード

```julia
@addmethod func(args...;kwargs...) = something
```

は、Plutoノートブックから呼び出されたときに単に次のように翻訳されます。

```julia
DefiningModule.func(args...;kwargs...) = something
```

そして、Plutoの外部から呼び出されたときには次のようになります。

```julia
func(args...;kwargs...) = something
```

これは、Pluto内での複数定義エラーを回避するのに役立ちますが、`@addmethod`でメソッドを定義しても、修正された関数を呼び出すすべてのセルのリアクティブな実行がトリガーされないという欠点があります。これは、`@addmethod`呼び出しを含むセルを削除すると、`DefiningModule`に追加された実際のメソッドがPlutoによって自動的に消去されず、同じシグネチャを持つ別のメソッドで上書きされるまでアクセス可能であることを意味します。

`@frompackage`/`@fromparent`で読み込まれたモジュールにメソッドを追加する場合は、モジュールを再読み込みするだけでハングしたメソッドを削除できるため、これは簡単に修正できます。

例についてはこのビデオを参照してください：

![Link to Video](https://user-images.githubusercontent.com/12846528/236472989-da86a311-4501-4966-9f0b-1298bbd9d53b.mp4)

また、次も参照してください： [`@frompackage`](@ref), [`@fromparent`](@ref)
