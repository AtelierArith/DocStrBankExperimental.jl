```julia
function studentMcTestRM(<same args and kwargs as `studentMcTest1S`>)
```

実際には[`studentMcTest1S`](@ref)のエイリアスです。

反復測定のための多重比較t検定を実行するには、2つの測定（または処置、時間など）間の差の$M$ベクトルのベクトルをデータ入力として使用します。

`refmean`のデフォルト値は変更しないでください。詳細については[`studentMcTest1S`](@ref)を参照してください。

*方向性検定、置換スキームおよび正確な検定のための置換回数:* [`studentTest1S`](@ref)に従って

*単変量バージョン:* [`studentTestRM`](@ref)

*エイリアス:* `tMcTestRM`

[MultcompTest](@ref)構造体を返します。

*例*

```julia
using PermutationTests
N=10 # 処置ごとの観測数
M=100 # 仮説の数

# データが次のようになっていると仮定します
Y1=[randn(N) for m=1:M]; # 測定1
Y2=[randn(N) for m=1:M]; # 測定2

# 差を計算しましょう
Y=[y1-y2 for (y1, y2) in zip(Y1, Y2)];
t=tMcTestRM(Y) # デフォルトでは検定は双方向です

tR=tMcTestRM(Y; direction=Both()) # 右方向の検定
# 検定tRがいくつかの仮説に対して有意である場合、 
# これらの仮説に対して測定1の平均が 
# 測定2の平均を超えます。
```
