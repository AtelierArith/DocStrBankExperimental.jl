```
GetArgLength(F::Function; max::Int=100) -> Int
```

`F`の入力構造、すなわち`Number`または`AbstractVector`を受け入れるかどうか、またその長さを判断しようとします。これは、`rand(i)`で関数を順次評価し、評価がエラーを投げなくなるまで続けることで達成されます。その結果、`GetArgLength`は`F`が`rand(i)`でエラーを出す場合、正しい入力構造を判断できません。

!!! note
    長さ1の`Real`と`Vector{Real}`を区別しません。すなわち、`Real`↦`+1`です。これら2つのオプションを区別するには、代わりに`_GetArgLength()`を使用してください。

