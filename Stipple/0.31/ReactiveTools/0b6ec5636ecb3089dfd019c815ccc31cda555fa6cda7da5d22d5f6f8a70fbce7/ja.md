```julia
@page(url, view; model::Union{Module, Type{<:ReactiveModel}, ReactiveModel},
                layout::Union{Genie.Renderers.FilePath,<:AbstractString,ParsedHTMLString,Nothing,Function} = nothing
                debounce::Int = Stipple.JS_DEBOUNCE_TIME,
                throttle::Int = Stipple.JS_THROTTLE_TIME,
                core_theme::Bool = true,
                pre::Union{Function, Vector{<:Function}} = Function[],
                post::Union{Function, Vector{<:Function}} = Function[])
```

`view`でソースを持つ新しいページを`url`のルートでレンダリングするために登録します。

**使用法**

```julia
@page("/", "view.html")

@page("/", ui; model = MyApp) # 明示的なアプリを指定するため
```

### その他のパラメータ

  * `debounce`: ms単位のデバウンスタイム
  * `throttle`: ms単位のスロットルタイム
  * `core_theme`: コアテーマを使用するかどうか
  * `pre`: 認証などのための事前レンダリング関数

    関数定義: `pre1() = println("pre1")`.

    呼び出し: `@page("/", ui, pre = pre1)` または `@page("/", ui, pre = [pre1, pre2, ...])`

    関数の結果が`nothing`でない場合、レンダリングは停止し、結果が返されます。
  * `post`: モデルの初期値の変更などのための事後レンダリング関数

    関数定義:

    `@handler function post1();      println("post1");      x = new_x;      println("changed initial value of :x to new_x");  end`   モデル変数はアクセス可能で、事後レンダリング関数内で変更できます。詳細については[`@handler`](@ref)を参照してください。モデルが準備完了後に変数を更新するには、モデルハンドラ`@onchange isready @push`または`@onchange isready @push x`が必要です。
