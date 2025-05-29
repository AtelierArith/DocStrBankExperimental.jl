```julia
function pointBiSerialTest(<same args and kwargs as `studentTestIS`>)
```

実際には [`studentTestIS`](@ref) のエイリアスです。

データの置換による単変量 [ポイントバイセリアル相関テスト](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient)。相関は、要素数 $N=N_1+N_2$ の入力ベクトル `y` と、最初の $N_1$ 要素が `1`、残りの $N_2$ 要素が `2` に等しい内部的に作成されたベクトル $x$ の間にあります。二項変数 $x$ に他の値を使用したり、その要素の順序を変更する必要がある場合は、代わりに [`correlationTest`](@ref) を使用してください。

帰無仮説は次の形を持ちます。

$$
H_0: b_{(x,y)}=0
$$

、

ここで $b_{(x,y)}$ は入力データベクトル `y` と内部的に作成されたベクトル $x$ の間のポイントバイセリアル相関です。

方向性テスト、置換スキーム、および正確なテストのための置換回数：[`studentTestIS`](@ref) に従います。

*多重比較バージョン:* [`pointBiSerialMcTest`](@ref)

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
ns=[4, 6] # グループ1とグループ2の観測数 (N1 と N2)
N=sum(ns) # 観測の総数

y = rand(N) # 例としてのいくつかのガウスデータ
# 暗黙的に、ポイントバイセリアル相関は 
# y と x=[1, 1, 1, 1, 2, 2, 2, 2, 2, 2] の間にあります
t=pointBiSerialTest(y, ns) # デフォルトではテストは双方向です

tR=pointBiSerialTest(y, ns; direction=Right()) # 右方向のテスト
tL=pointBiSerialTest(y, ns; direction=Left()) # 左方向のテスト
```
