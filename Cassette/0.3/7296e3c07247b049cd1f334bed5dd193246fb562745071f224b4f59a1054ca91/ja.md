```
overdub(context::Context, f, args...)
```

`context`に関してオーバーダブされた`f(args...)`を実行します。

より具体的には、`f(args...)`を実行しますが、内部メソッド呼び出し`g(x...)`は次のような文に置き換えられます：

```
begin
    prehook(context, g, x...)
    overdub(context, g, x...) # %n
    posthook(context, %n, g, x...)
    %n
end
```

それ以外の場合、Cassetteが`f(args...)`のメソッド本体の低下したIRを取得できない場合は、代わりに`fallback(context, f, args...)`が呼び出されます。Cassetteの[`canrecurse`](@ref)関数は、これが発生するかどうかを確認するための便利なユーティリティです。

注入された`prehook`/`posthook`文があなたのユースケースに必要ない場合は、[`disablehooks`](@ref)関数を介してその注入を無効にできます。

さらに、実行トレースで遭遇したすべてのメソッド本体に対して、存在する場合は`context`に関連付けられたコンパイラーパスを適用します。このユーザー提供のパスは、メソッド呼び出しが上記の形式に変換される前にメソッドIRに対して実行されることに注意してください。詳細については、[`@pass`](@ref)マクロを参照してください。

`Cassette.hastagging(typeof(context))`が真である場合、タグ付き値の伝播に対応するためにいくつかの追加パスが実行されます：

  * `Expr(:new)`は`Cassette.tagged_new`への呼び出しに置き換えられます
  * `Expr(:splatnew)`は`Cassette.tagged_splatnew`への呼び出しに置き換えられます
  * `Expr(:gotoifnot)`に渡される条件付き値はタグが外されます
  * `Expr(:foreigncall)`への引数はタグが外されます
  * 外部モジュールバインディングへのロード/ストアはタグ付けシステムによってインターセプトされます

`overdub`のデフォルト定義は、与えられた関数に再帰的に入ってオーバーダブを続けることですが、特定のコンテキストおよび/またはメソッドシグネチャに関して`overdub`をオーバーロードすることで、この再帰を中断/リダイレクトして新しいコンテキスト実行プリミティブを定義できます。例えば：

```
julia> using Cassette

julia> Cassette.@context Ctx;

julia> Cassette.overdub(::Ctx, ::typeof(sin), x) = cos(x)

julia> Cassette.overdub(Ctx(), x -> sin(x) + cos(x), 1) == 2 * cos(1)
true
```

参照：[`recurse`](@ref), [`prehook`](@ref), [`posthook`](@ref)
