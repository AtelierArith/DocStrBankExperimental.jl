```
@composed
```

複数の `Possibility` を1つに構成する方法で、関数を適用します。

戻り値の型は最善の努力として推測されます！

次のように使用します：

```julia-repl
julia> using Supposition, Supposition.Data

julia> text = Data.Text(Data.AsciiCharacters(); max_len=10)

julia> gen = Supposition.@composed function foo(a = text, num=Data.Integers(0, 10))
              lpad(num, 2) * ": " * a
       end

julia> example(gen)
" 8:  giR2YL\rl"
```

上記のように全体の `function` を渡すことに加えて、次の構文もサポートされています：

```julia
# 名前が必要ない場合は、匿名関数を使用
double_up =  @composed (a = text) -> a*a
prepend_foo = @composed (a = text,) -> "foo: "*a
expo_str = @composed (a = text, num = Data.Integers(0,10)) -> a^num

# ..または、匿名関数にも名前を付けることができます - 上記の3つすべてで機能します
sentence = @composed build_sentence(a = text, num = Data.Floats{Float16}()) -> "The $a is $num!"
build_sentence("foo", 0.5) # "The foo is 0.5!" を返します

# 既存の関数から新しいジェネレーターを構成することもできます
my_func(str, number) = number * "? " * str
ask_number = @composed my_func(text, num)
```
