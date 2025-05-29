異なるノード間にブランチを接続し、ノード間のポテンシャルとフローを指定するためのヘルパーモデル。

[RefBranch](#refbranch)も参照してください。

```julia
Branch(n1, n2, v, i)
```

### 引数

  * `n1` : 正の基準ノード。
  * `n2` : 負の基準ノード。
  * `v` : ノード間のポテンシャル変数。
  * `i` : ノード間のフロー変数。

### 戻り値

  * 各ノードのRefBranchエントリと、`v`を`n1 - n2`に割り当てる方程式からなるモデル。

### 参考文献

このノード記述は[David Broman](http://web.ict.kth.se/~dbro/)の研究に基づいています。以下を参照してください：

  * http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-173.pdf
  * http://www.bromans.com/software/mkl/mkl-source-1.0.0.zip
  * https://github.com/david-broman/modelyze

### 例

標準ライブラリにおける電気抵抗器の定義は次のとおりです：

```julia
function Resistor(n1::ElectricalNode, n2::ElectricalNode, R::Signal)
    i = Current(compatible_values(n1, n2))
    v = Voltage(value(n1) - value(n2))
    [
        Branch(n1, n2, v, i)
        v ~ R .* i
    ]
end
```
