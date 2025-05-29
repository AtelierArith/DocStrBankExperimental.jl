```
@check [key=val]... function...
```

プロパティベースのテストを宣言して実行する主な方法。次のように呼び出します：

```julia-repl
julia> using Supposition, Supposition.Data

julia> Supposition.@check [options...] function foo(a = Data.Text(Data.Characters(); max_len=10))
          length(a) > 8
       end
```

サポートされているオプションは、`key=value`として渡されます：

  * `rng::Random.AbstractRNG`: 使用するRNGを渡します。デフォルトは`Random.Xoshiro(rand(Random.RandomDevice(), UInt))`です。
  * `max_examples::Int`: プロパティに渡される生成された例の最大数。
  * `broken::Bool`: 通過すべきだが通過しないプロパティを壊れたものとしてマークし、失敗がカウントされないようにします。
  * `record::Bool`: 呼び出しの結果を親テストセットと共に記録するかどうか。
  * `db`: ブール値（`true`はフォールバックデータベースを使用、`false`は例の記録を停止）または[`ExampleDB`](@ref)。
  * `config`: すべての前のオプションのデフォルトとして使用される`CheckConfig`オブジェクト。`@check`に明示的に渡されたオプションは、`config`を通じて提供されたものを上書きします。

指定された関数への引数は、ジェネレーター戦略であることが期待されます。バインドされる名前は、テスト内で生成されたオブジェクトが持つ名前です。これらの引数は、プロパティが失敗した場合に表示されます！

# 拡張ヘルプ

## 既存のプロパティの再利用

すでに定義された述語がある場合、`@check`で呼び出し構文を使用することもできます。ここでは、ジェネレーターが指定された関数に純粋に位置的に渡されます。引数名は必要ありません。

```julia-repl
julia> using Supposition, Supposition.Data

julia> isuint8(x) = x isa UInt8

julia> intgen = Data.Integers{UInt8}()

julia> Supposition.@check isuint8(intgen)
```

## カスタムRNGの渡し方

ランダムデータ生成に使用されるカスタムRNGオブジェクトをオプションで指定することが可能です。指定がない場合は、`Xoshiro(rand(Random.RandomDevice(), UInt))`が代わりに使用されます。

```julia-repl
julia> using Supposition, Supposition.Data, Random

# カスタムXoshiroインスタンスを使用
julia> Supposition.@check rng=Xoshiro(1234) function foo(a = Data.Text(Data.Characters(); max_len=10))
          length(a) > 8
       end
```

!!! warning "ハードウェアRNG"
    ハードウェアRNGを`@check`に直接渡すことはできないことに注意してください。ハードウェアエントロピーに基づいてランダム化したい場合は、ハードウェアRNGからコピー可能なRNG（例えば`Xoshiro`）をシードし、それを`@check`に渡してください。RNGは再現性のためにコピー可能である必要があります。


## 追加の構文

上記のように`function`全体を渡すことに加えて、次の構文もサポートされています：

```julia
text = Data.Text(Data.AsciiCharacters(); max_len=10)

# 名前が必要ない場合は、匿名関数を使用
@check (a = text) -> a*a
@check (a = text,) -> "foo: "*a
@check (a = text, num = Data.Integers(0,10)) -> a^num

# ..または匿名関数にも名前を付けることができます - 上記の3つすべてで機能します
@check build_sentence(a = text, num = Data.Floats{Float16}()) -> "The $a is $num!"
build_sentence("foo", 0.5) # "The foo is 0.5!"を返します
```

!!! warning "再生可能性"
    匿名関数を`@check`に渡すことはできますが、周囲の`@check`の呼び出しが移動されたときに見つかったテストケースの再生可能性が妨げられる可能性があることに注意してください。名前付き関数のみがこれに対して耐性があります。

