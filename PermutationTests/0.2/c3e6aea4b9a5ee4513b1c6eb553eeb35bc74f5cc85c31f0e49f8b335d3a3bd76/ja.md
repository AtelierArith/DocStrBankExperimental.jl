```julia
function pointBiSerialMcTest(<same args and kwargs as `studentMcTestIS`>)
```

実際には [`studentMcTestIS`](@ref) のエイリアスです。

$$
M
$$

個の [ポイントバイセリアル相関テスト](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient) を同時に実行します。相関は、引数 `Y` として与えられた $M$ 個の入力データベクトル $y_1,...,y_M$ の間で、すべて $N=N_1+N_2$ 要素を持ち、内部的に作成されたベクトル $x$ との間で行われます。このベクトル $x$ の最初の $N_1$ 要素は `1` に等しく、残りの $N_2$ 要素は `2` に等しくなります。

二項変数 $x$ に他の値を使用したり、その要素の順序を変更したい場合は、代わりに [`correlationMcTest`](@ref) を使用してください。

$$
M
$$

個の帰無仮説は次の形を持ちます。

$$
H_0(m): b_{(x,y_m)}=0, \quad m=1...M
$$

,

ここで $b_{(x,y_m)}$ は、`Y` の $m^{th}$ 入力データベクトル $y_m$ と内部的に作成されたベクトル $x$ との間のポイントバイセリアル相関です。

*方向性テスト、置換スキームおよび正確なテストのための置換回数:* *単変量バージョン* [`pointBiSerialTest`](@ref) に従います。

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
ns=[4, 6]; # N1=4, N2=6
N=sum(ns); # 観測数

Y = [rand(N) for m=1:M]; # 例としてのいくつかのガウスデータ
# 暗黙的に、ポイントバイセリアル相関は 
# y1,...,yM と x=[1, 1, 1, 1, 2, 2, 2, 2, 2, 2] の間にあります
t=pointBiSerialMCTest(Y, ns) # デフォルトではテストは双方向です
```

```julia
tR=pointBiSerialMCTest(Y, ns; direction=Right()) # 右方向テスト
tL=pointBiSerialMCTest(Y, ns; direction=Left()) # 左方向テスト
```
