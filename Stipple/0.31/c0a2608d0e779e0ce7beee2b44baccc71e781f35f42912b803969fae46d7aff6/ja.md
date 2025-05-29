```
synchronize!(o1::AbstractObservable, o2::AbstractObservable; priority::Union{Int,Nothing} = nothing, update = true, biderectional = false)
```

2つのオブザーバブルを同期させ、`o1`の値を`o2`の値に設定します。`connect!()`とは異なり、この関数はループバックを作成せずに双方向で動作します。複数のオブザーバブルを同期させることも可能ですが、常に同じルートオブザーバブルに同期させるように注意が必要です。

### パラメータ

  * `o1::AbstractObservable`: 同期させる最初のオブザーバブル。
  * `o2::AbstractObservable`: 同期させるオブザーバブル
  * `priority::Union{Int,Nothing}`: 同期リスナーの優先度。

    優先度は同期ペアの識別子として使用されます。複数のオブザーバブルが同期される場合、異なる優先度を持つ必要があります。`nothing`（デフォルト）の場合、`synchronize!()`呼び出しの順序と同じ順序になるように一意の優先度を検索します。
  * `update::Bool`: `true`の場合、`o1`は`o2`の値で更新されます。デフォルト: `true`
  * `biderectional`: `true`（デフォルト）の場合、双方向同期を実行し、`false`の場合は`o1`が`o2`に従うように同期します。後者は`connect!()`と機能的に同じですが、`unsynchronize!()`は`synchronize!()`で同期された変数に対してのみ正しく動作します。

### 例 1

```
o = Observable(0)
on(o -> println("o: $o"), o)

o1 = Observable(1)
on(o1 -> println("o1: $o1"), o)

o2 = Observable(2)
on(o2 -> println("o2: $o2"), o)

synchronize!(o1, o)
synchronize!(o2, o)

o[] = 10;
# o: 10
# o1: 10
# o2: 10

o1[] = 11;
# o: 11
# o1: 11
# o2: 11

o2[] = 12;
# o: 12
# o1: 12
# o2: 12
```

### 例 2

```
using Stipple, Stipple.ReactiveTools
using StippleUI

const X = Observable(0)

@app Observer begin
    @in x = 0

    @onchange isready begin
        synchronize!(__model__.x, X)
    end
end

@event Observer :finalize begin
    println("unsynchronizing ...")
    @info unsynchronize!(__model__.x)
    notify(__model__, Val(:finalize))
end

@page("/", slider(1:100, :x), model = Observer)

@debounce Observer x 0
@throttle Observer x 10

up()
```

### 例 3

例 2の修正で、同じセッションID（すなわち、同じブラウザ）を持つタブのみを同期します。

```
using Stipple, Stipple.ReactiveTools
using StippleUI
using GenieSession

const XX = Dict{String, Reactive}()

@app Observer begin
    @in x = 0
    @private session = ""

    @onchange isready begin
        r = get!(XX, session, R(x))
        synchronize!(__model__.x, r)
    end
end

@page("/", slider(1:100, :x), model = Observer, post = model -> begin model.session[] = session().id; nothing end)

@event Observer :finalize begin
    println("unsynchronizing ...")
    @info unsynchronize!(__model__.x)
    notify(__model__, Val(:finalize))
end

@debounce Observer x 0
@throttle Observer x 10

up()
```

`post`がセッションIDをモデルに添付するために使用されていることに注意してください。添付された関数が何も返さないことを確認して、ページのレンダリングを続行できるようにしてください。`post`が値を返すと、ページはページコンテンツの代わりにその値をレンダリングします。詳細については[`@page`](@ref)を参照してください。

イベント`:finalize`を介した非同期化は、ページのリロードやナビゲーションによって置き換えられたモデルへの同期を抑制するために重要です。
