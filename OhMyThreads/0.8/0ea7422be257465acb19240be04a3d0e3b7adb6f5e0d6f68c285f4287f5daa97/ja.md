```
@allow_boxed_captures expr
```

デフォルトでは、OhMyThreads.jlはローカル変数を参照するマルチスレッドコードを検出し、エラーを出します。これは、変数が複数のスコープで再バインドされる可能性がある場合に「ボックス化」されるためです。このプロセスは、サイレントレースコンディションを引き起こすことによって、マルチスレッドコードに非常に微妙なバグを引き起こす可能性があります。例えば：

```julia
let
    function wrong()
        tmap(1:10) do i
            A = i # Aを初めて定義する（レキシカルに）
            sleep(rand()/10)
            A # ユーザーはローカルのAのみを参照しようとしている
        end
    end
    @show wrong()
    A = 1 # ボックス化！これにより「A」が`wrong`内の同じ変数に持ち上げられますが、ユーザーは新しいものを望んでいたと思われます
end
```

この例では、`[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`が得られることを期待するかもしれませんが、実際には`A`が「ボックス化」されているため、正しくない結果が観察されます。これを修正するには、次のように書く必要があります。

```julia
let
    function right()
        tmap(1:10) do i
            local A = i
            sleep(rand()/10)
            A 
        end
    end
    @show right()
    A = 1
end
```

ただし、OhMyThreadsのエラーメカニズムをバイパスしたい場合は、`@allow_boxed_captures`を使用して、問題ないと考えるコードをラップすることができます。例えば：

```julia-repl
julia> let A = 1 
           @allow_boxed_captures tmap(1:10) do i
               A = i
               sleep(rand()/10)
               A # レースコンディション！
           end
       end
10-element Vector{Int64}:
 4
 2
 7
 2
 2
 8
 6
 8
 7
 2
```

これは動的スコープの構造であるため、この効果は`expr`内の*すべての*ネストされたコードに適用されます。

また、`@disallow_boxed_captures`も参照してください。
