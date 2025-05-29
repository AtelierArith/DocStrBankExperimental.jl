```
makeGlobalGrid!(tsg::TasmanianSG; type, rule, anisotropic_weights=Vector{Int32}(undef, 0), alpha=0.0, beta=0.0, custom_filename="", level_limits=Vector{Int32}(undef, 0))
```

は、`tsg`によって保持されている既存のグリッドを破棄し、グローバル多項式ルールを使用して新しいスパースグリッドを作成します。

type: テンソル選択戦略を識別する文字列      `level`     `curved`     `hyperbolic`     `tensor`      `iptotal`   `ipcurved`   `iphyperbolic`   `iptensor`      `qptotal`   `qpcurved`   `qphyperbolic`   `qptensor`

rule: グリッドを誘導する1-Dルールを定義する文字列

```
   補間ルール

      注: これらのルールによって誘導される数値積分は
            補間関数を統合することによって構築されます

      `clenshaw-curtis`    `clenshaw-curtis-zero`      `fejer2`
      `rleja`    `rleja-odd`  `rleja-double2`   `rleja-double4`
      `rleja-shifted`   `rleja-shifted-even`
      `max-lebesgue`    `max-lebesgue-odd`
      `min-lebesgue`    `min-lebesgue-odd`
      `leja`            `leja-odd`
      `min-delta`       `min-delta-odd`

      `chebyshev`       `chebyshev-odd`
        チェビシェフ多項式の根を使用した近似
        非ネストケース（クレンズホー・カーティスノードとは対照的）

   数値積分ルール、重みは可能な限り
                     最高の多項式次数に対する正確さを目指します

       `gauss-legendre`  `gauss-legendre-odd`
        測度が一様な直交多項式の根を使用した近似

       `gauss-patterson`  （別名、ネストされたガウス・レジェンドル）
        注: ノードと重みはハードコーディングされているため
        最高の深さに制限があります

       `gauss-chebyshev1`  `gauss-chebyshev1-odd`
       `gauss-chebyshev2`  `gauss-chebyshev2-odd`
         測度 1/sqrt(1-x^2) および sqrt(1-x^2) で直交する多項式の根を使用した近似

      `gauss-gegenbauer`  `gauss-gegenbauer-odd`
        測度 (1-x^2)^alpha で直交する多項式の根を使用した近似

      `gauss-jacobi`
        測度 (1-x)^alpha * (1+x)^beta で直交する多項式の根を使用した近似

      `gauss-laguerre`
        測度 x^alpha * epx(-x) で直交する多項式の根を使用した近似

      `gauss-hermite`  `gauss-hermite-odd`
        測度 |x|^alpha * epx(-x^2) で直交する多項式の根を使用した近似
```

anisotropic_weights: 重みのリストまたは配列 (Int)                      長さは次元または2*次元でなければならない                      最初の次元の重みは正でなければならない                      詳細はマニュアルを参照

alpha, beta: Float64       alpha : Gegenbauer、Jacobi、                Hermite および Laguerre ルールのための alpha パラメータ       beta  : Jacobi ルールのための beta パラメータ

custom_filename: カスタムタブ化されたルールを持つファイルへのパスを示す文字列
