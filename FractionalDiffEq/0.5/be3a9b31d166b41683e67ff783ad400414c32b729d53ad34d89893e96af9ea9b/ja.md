# 使用法

```
solve(FDDE::FDDEProblem, dt, DelayPECE())
```

遅延予測修正法を使用して、カプトの意味で遅延分数微分方程式問題を解決します。

単一項FDDEと複数FDDEの両方を解決でき、もちろん時間変動遅延もサポートしています😋。

## 参考文献

@article{Wang2013ANM, title={遅延分数階微分方程式のための数値法}, author={Zhen Wang}, journal={J. Appl. Math.}, year={2013}, volume={2013}, pages={256071:1-256071:7} }

@inproceedings{Nagy2014NUMERICALSF, title={可変階分数非線形遅延微分方程式の数値シミュレーション}, author={Abdelhameed M. Nagy and Taghreed Abdul Rahman Assiri}, year={2014} }

@inproceedings{Abdelmalek2019APM, title={複数遅延を持つ分数遅延微分系のための予測修正法}, author={Salem Abdelmalek and Redouane Douaifia}, year={2019} }
