```
@imcheck expr
```

上流の `IM_CHECK()` マクロのポートです。上流のマクロと同様に、`expr` が `false` に評価されると、呼び出し元の関数から早期に戻ります。`@test` よりもこれを使用することをお勧めします。なぜなら、テストエンジンにテスト結果を登録するため、組み込みのテストエンジンウィンドウを使用している場合に便利だからです（[`ShowTestEngineWindows()`](@ref) を参照）。

`@imcheck` はデフォルトで `@testset` にフックされるため、失敗はあなたの Julia `Test` テストとテストエンジンの両方に記録されます。これが望ましくない場合は、`jltest=false` を渡すことで無効にできます。

!!! note
    現在の実装の制限は、等式の両方の引数を表示するために式を適切に解析することがサポートされていないことです。


# 例

```julia
engine = te.CreateContext()
@register_test(engine, "foo", "bar") do ctx
    # これは `Test` とテストエンジンの両方に結果を記録します
    @imcheck false

    # これはテストエンジンのみに結果を記録します
    @imcheck false jltest=false
end
```
