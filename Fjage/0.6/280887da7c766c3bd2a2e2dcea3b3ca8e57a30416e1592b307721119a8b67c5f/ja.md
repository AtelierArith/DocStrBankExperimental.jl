```
CoroutineBehavior(action)
```

明示的な中断を可能にする振る舞いを作成します。

与えられた関数 `action(a::Agent, b::Behavior)` は、最も早い利用可能な機会に正確に1回呼び出されます。この振る舞いは、`delay(b, millis)` を呼び出すことによって明示的に自分自身を中断することができ、これにより振る舞いは `millis` ミリ秒の間直ちにブロックされます。

# 例:

```julia
@agent struct MyAgent end

function Fjage.startup(a::MyAgent)
  add(a, CoroutineBehavior() do a, b
    for ith = ("first", "second", "third")
      println("Pausing for the $ith time")
      delay(b, 500)
    end
  end)
end
```
