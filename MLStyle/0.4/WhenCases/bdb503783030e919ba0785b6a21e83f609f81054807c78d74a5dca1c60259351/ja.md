1. `let`構文のバインディングシーケンスでのデストラクチャリングを許可します。

バインディングシーケンスでは、

  * `a = b`や`f(x) = y`の形のバインディングは、ここではパターンマッチングと見なされます。
  * `@inline f(x) = 1`のような他のものは、元のletバインディングと同じで（パターンマッチングではありません）。

```julia
    @when let (a, 1) = x,
          [b, c, 5] = y
        (a, b, c)
    end
```

2. 通常の代入の場合、例えば

```julia
    @when (a, 2) = x begin
        # 何かをする
    end
```

これは次のように異なるものではありません。

```julia
    @match x begin
        (a, 2) => # 何かをする
        _ => nothing
    end
```

3. 複数のブランチの場合、次のようにできます。

```julia
x = 1
@when let (_, _) = x
    :tuple
@when begin ::Float64 = x end
    :float
@when ::Int = x
    :int
@otherwise
    :unknown
end
```

4. また、マッチング時に`cond.?`または`if cond end`の形で述語を使用できます：

```julia
x = 1
y = (1, 2)
cond1 = true
cond2 = true
@when let cond1.?,
          (a, b) = x
    a + b
@when begin if cond2 end
            (a, b) = y
      end
    a + b
end
```
