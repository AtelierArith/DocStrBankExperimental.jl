![Agents.jl](https://github.com/JuliaDynamics/JuliaDynamics/blob/master/videos/agents/agents4_logo.gif?raw=true)

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaDynamics.github.io/Agents.jl/stable) [![](https://img.shields.io/badge/DOI-10.1177/00375497211068820-purple)](https://journals.sagepub.com/doi/10.1177/00375497211068820) [![CI](https://github.com/JuliaDynamics/Agents.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/Agents.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/Agents.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/Agents.jl) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![Package Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FAgents&query=total_requests&label=Downloads)](http://juliapkgstats.com/pkg/Agents)

Agents.jlは、エージェントベースのモデリング（ABM）のための純粋な[Julia](https://julialang.org/)フレームワークです。これは、自律エージェントが事前に定義されたルールのセットに基づいて、他のエージェントを含む環境に反応する計算シミュレーション手法です。Agents.jlの主なハイライトは以下の通りです：

1. 高速です（MASON、NetLogo、またはMesaよりも速い）
2. シンプルです：非常に短い学習曲線を持ち、最小限のコードを書く必要があります
3. 数千の即使用可能なエージェントアクションの広範なインターフェースを持っています
4. Open Street Maps上でのシミュレーションを簡単に行えます
5. 従来の離散時間ABMシミュレーションと、連続時間の「イベントキューに基づく」ABMシミュレーションの両方を許可します。

詳細情報と機能の広範なリストは、[オンライン](https://juliadynamics.github.io/Agents.jl/stable/)で見つけるか、`docs/make.jl`ファイルを実行してローカルにビルドすることで見つけることができます。

## 引用

このパッケージを出版物で使用する場合、または単に参照したい場合は、以下の論文を引用してください：

```
@article{Agents.jl,
  doi = {10.1177/00375497211068820},
  url = {https://doi.org/10.1177/00375497211068820},
  year = {2022},
  month = jan,
  publisher = {{SAGE} Publications},
  pages = {003754972110688},
  author = {George Datseris and Ali R. Vahdati and Timothy C. DuBois},
  title = {Agents.jl: a performant and feature-full agent-based modeling software of minimal code complexity},
  journal = {{SIMULATION}},
  volume = {0},
  number = {0},
}
```
