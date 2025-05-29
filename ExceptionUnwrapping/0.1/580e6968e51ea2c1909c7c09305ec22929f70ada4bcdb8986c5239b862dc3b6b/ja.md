```
@test_throws_wrapped exception expr
```

`Test.@test_throws`に似ていますが、これは式`expr`が`exception`をスローするか、または`exception`を*ラップ*する式をスローすることをテストします。

ユーザーは、例外がラップされているかどうかを気にしない場合、この関数を使用できます。たとえば、ユーザーが並行性を使用しているかどうかを気にしない場合です。

# 例

```jldoctest
julia> @test_throws_wrapped BoundsError [1, 2, 3][4]
テストに合格しました
      スローされた: BoundsError

julia> @test_throws_wrapped DimensionMismatch fetch(@async [1, 2, 3] + [1, 2])
テストに合格しました
      スローされた: DimensionMismatch
```
