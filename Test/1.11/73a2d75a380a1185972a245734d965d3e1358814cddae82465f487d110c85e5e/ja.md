```
@test_broken ex
@test_broken f(args...) key=val ...
```

現在一貫して失敗するべきテストを示します。式 `ex` が `false` に評価されるか、例外を引き起こすことをテストします。もしそうであれば `Broken` `Result` を返し、式が `true` に評価される場合は `Error` `Result` を返します。これは [`@test ex broken=true`](@ref @test) と同等です。

`@test_broken f(args...) key=val...` の形式は `@test` マクロと同様に機能します。

# 例

```jldoctest
julia> @test_broken 1 == 2
テストが壊れました
  式: 1 == 2

julia> @test_broken 1 == 2 atol=0.1
テストが壊れました
  式: ==(1, 2, atol = 0.1)
```
