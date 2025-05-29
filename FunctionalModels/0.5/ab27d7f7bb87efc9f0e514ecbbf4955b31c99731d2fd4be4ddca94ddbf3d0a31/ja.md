特別なModelTypeで、ノードへのブランチフローを指定します。モデルがフラット化されると、ノードへのブランチフローをゼロにするための方程式が作成されます。

[Branch](#branch)も参照してください。

```julia
RefBranch(n, i) 
```

### 引数

  * `n` : 参照ノード。
  * `i` : このノードに関連するフローバリアブル。

### 参考文献

このノードの説明は、[David Broman](http://web.ict.kth.se/~dbro/)の研究に基づいています。以下を参照してください：

  * http://www.eecs.berkeley.edu/Pubs/TechRpts/2012/EECS-2012-173.pdf
  * http://www.bromans.com/software/mkl/mkl-source-1.0.0.zip
  * https://github.com/david-broman/modelyze

[Modelyze](https://github.com/david-broman/modelyze)には、`RefBranch`と`Branch`の両方があります。

### 例

以下は、標準ライブラリのHeatCapacitorの定義で使用されるRefBranchの例です。`hp`は参照ノード（HeatPort、別名温度）で、`Q_flow`はフローバリアブルです。

```julia
function HeatCapacitor(hp::HeatPort, C::Signal)
    Q_flow = HeatFlow(compatible_values(hp))
    [
        RefBranch(hp, Q_flow)
        der(hp) ~ Q_flow ./ C
    ]
end
```

以下は、2つのノード間に電流（フローバリアブル）を注入するモデルの標準ライブラリからのSignalCurrentの定義です：

```julia
function SignalCurrent(n1::ElectricalNode, n2::ElectricalNode, I::Signal)  
    [
        RefBranch(n1, I) 
        RefBranch(n2, -I) 
    ]
end
```
