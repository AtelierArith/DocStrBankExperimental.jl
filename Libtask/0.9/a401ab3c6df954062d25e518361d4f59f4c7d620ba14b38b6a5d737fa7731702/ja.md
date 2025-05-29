```
TapedTask(taped_globals::Any, f, args...; kwargs...)
```

指定された `taped_globals`、関数 `f`、位置引数 `args`、およびキーワード引数 `kwargs` を使用して `TapedTask` を構築します。

# 拡張ヘルプ

`TapedTask` の中心的な機能は3つあり、3つの例を通じて示します。

## 再開

関数 [`Libtask.produce`](@ref) は Libtask において特別な意味を持ちます。これを通常の Julia 関数の任意の場所に挿入できます。例えば

```jldoctest tt
julia> function f()
           for t in 1:2
               produce(t)
               t += 1
           end
           return nothing
       end
f (generic function with 1 method)
```

`f` から `TapedTask` を構築し、[`Libtask.consume`](@ref) を呼び出すと、次のようになります。

```jldoctest tt
julia> t = TapedTask(nothing, f);

julia> consume(t)
1
```

この意味は、[`Libtask.consume`](@ref) が関数 `f` を実行し、[`Libtask.produce`](@ref) への呼び出しに達するまで実行され、その時点で [`Libtask.produce`](@ref) への引数を返すということです。

その後の [`Libtask.produce`](@ref) への呼び出しは、最後にヒットした [`Libtask.produce`](@ref) ステートメントの直後から `f` の実行を*再開*します。

```jldoctest tt
julia> consume(t)
2
```

ヒットする [`Libtask.produce`](@ref) ステートメントがもうない場合、[`Libtask.consume`](@ref) を呼び出すと `nothing` が返されます：

```jldoctest tt
julia> consume(t)

```

## コピー

[`TapedTask`](@ref) はコピーできます。これにより、完全に独立したオブジェクトが作成されます。例えば：

```jldoctest tt
julia> t2 = TapedTask(nothing, f);

julia> consume(t2)
1
```

コピーを作成し、その状態を進めると、元のものが生成するのと同じ値を生成します：

```jldoctest tt
julia> t3 = copy(t2);

julia> consume(t3)
2
```

さらに、コピーの状態を進めても元の状態は進んでいないため、完全に独立したコピーです：

```jldoctest tt
julia> consume(t2)
2
```

## TapedTask特有のグローバル変数

タスクのコピーと元のものが非常に特定の方法で異なることを許可することがしばしば望まれます。例えば、逐次モンテカルロの文脈では、2つのコピーの唯一の違いが乱数生成器であることを望むかもしれません。

これを達成するための一般的なメカニズムが利用可能です。[`Libtask.get_taped_globals`](@ref) と [`Libtask.set_taped_globals!`](@ref) を使用すると、特定の [`Libtask.TapedTask`](@ref) に特有の変数を設定および取得できます。前者は関数内で呼び出すことができます：

```jldoctest sv
julia> function f()
           produce(get_taped_globals(Int))
           produce(get_taped_globals(Int))
           return nothing
       end
f (generic function with 1 method)
```

[`Libtask.TapedTask`](@ref) への最初の引数は、[`Libtask.get_taped_globals`](@ref) が返す値です：

```jldoctest sv
julia> t = TapedTask(1, f);

julia> consume(t)
1
```

返される値は、[`Libtask.consume`](@ref) の呼び出しの間に変更できます：

```jldoctest sv
julia> set_taped_globals!(t, 2)

julia> consume(t)
2
```

ここでは `Int` が使用されていますが、[`Libtask.get_taped_globals`](@ref) が返す値を好きなものに設定することが許可されています。

# 実装ノート

内部では、元の関数に関連付けられた `IRCode` を取得し、それを変換して `produce` / `consume` インターフェースに必要なセマンティクスを実装し、実行可能にするために `MistyClosure` 内に配置することで `TapedTask` を実装します。

`IRCode` を変換する際の主な考慮事項は2つあります。1つ目は、`TapedTask` の「状態」をコピーできるようにすることです。これにより、`TapedTask` をコピーし、後で再開できるようになります。`TapedTask` の完全な状態は、その引数と各 ssa に関連付けられた値によって与えられます（これらは最初は未定義です）。ssa 値の状態をコピーできるようにするために、`TapedTask` を実装する `MistyClosure` のキャプチャに `Base.RefValue{T}` を配置します。これは IR 内の各 ssa に対して1つずつです（`T` はその ssa に対して推論された型です）。呼び出しは、これらの参照から ssa の値を読み込み、元の操作を適用し、命令に関連付けられた参照に結果を書き込むことによって置き換えられます。例えば、元の `IRCode` のスニペットが次のようなものである場合

```julia
%5 = f(%3, _1)
```

変換された IR は次のようになります。

```julia
%5 = ref_for_%3[]
%6 = f(%5, _1)
ref_for_%5[] = %6
```

このように設定することで、すべての参照をコピーするだけで独立したコピーが作成されることが保証されます。正確性のために `deepcopy` が必要です。なぜなら、参照は互いにエイリアスを持たない（構造上）ものの、その内容は持つ可能性があるからです。例えば、2つの参照が同じ `Array` を含む場合があり、一般的に関数の動作はこの関係に依存します。

変換の2つ目の要素は、`produce` メカニズムを実装し、生成した場所から計算を再開する能力です。大まかに言えば、`IRCode` は、`produce` 呼び出しが遭遇するたびに、`MistyClosure` が `produce` への引数を返し、その後の呼び出しが `produce` ステートメントの直後から計算を再開するように修正されなければなりません。この再開は、`produce` ステートメントの後に返す前にカウンタの値を設定することによって達成されます。このカウンタに対する一連の比較と、[`GotoIfNot`](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form) ステートメントが IR の先頭に挿入され、計算を再開すべきコードのポイントにジャンプします。これらは、`TapedTask` が最初に実行されるときに計算が最初のステートメントから始まるように設定されています。これは、上記で説明した参照メカニズムによっても促進され、呼び出し間で状態が持続することを保証します。

上記は `TapedTask` がどのように実装されているかの大まかな概要を示しています。実装の詳細を説明するために広範にコメントされたコードに興味のある読者を参照します。
