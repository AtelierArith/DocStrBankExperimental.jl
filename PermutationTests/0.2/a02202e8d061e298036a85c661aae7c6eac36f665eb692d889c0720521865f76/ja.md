```julia
function studentTestRM(<same args and kwargs as `studentTest1S`>)
```

データの置換による単変量 [t検定](https://en.wikipedia.org/wiki/Paired_difference_test) の反復測定。実際には [`studentTest1S`](@ref) のエイリアスです。

反復測定のt検定を実行するには、測定間の差のベクトルをデータ入力として使用します。

`refmean` のデフォルト値は変更しないでください。詳細については [`studentTest1S`](@ref) を参照してください。

**エイリアス:** `tTestRM`

*多重比較バージョン:* [`studentMcTestRM`](@ref)

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
y1=randn(10) # 測定1
y2=randn(10) # 測定2
t=tTestRM(y1.-y2) # デフォルトではテストは双方向です

tR=tTestRM(y1.-y2; direction=Both()) # 右方向のテスト
# テスト tR が有意であれば、測定1の平均は測定2の平均を超えます。
```
