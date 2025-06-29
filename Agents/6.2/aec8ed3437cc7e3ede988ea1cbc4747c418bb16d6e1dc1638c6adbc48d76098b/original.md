![Agents.jl](https://github.com/JuliaDynamics/JuliaDynamics/blob/master/videos/agents/agents4_logo.gif?raw=true)

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaDynamics.github.io/Agents.jl/stable) [![](https://img.shields.io/badge/DOI-10.1177/00375497211068820-purple)](https://journals.sagepub.com/doi/10.1177/00375497211068820) [![CI](https://github.com/JuliaDynamics/Agents.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/Agents.jl/actions?query=workflow%3ACI) [![codecov](https://codecov.io/gh/JuliaDynamics/Agents.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/JuliaDynamics/Agents.jl) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![Package Downloads](https://img.shields.io/badge/dynamic/json?url=http%3A%2F%2Fjuliapkgstats.com%2Fapi%2Fv1%2Ftotal_downloads%2FAgents&query=total_requests&label=Downloads)](http://juliapkgstats.com/pkg/Agents)

Agents.jl is a pure [Julia](https://julialang.org/) framework for agent-based modeling (ABM): a computational simulation methodology where autonomous agents react to their environment (including other agents) given a predefined set of rules. Some major highlights of Agents.jl are:

1. It is fast (faster than MASON, NetLogo, or Mesa)
2. It is simple: has a very short learning curve and requires writing minimal code
3. Has an extensive interface of thousands of out-of-the box possible agent actions
4. Straightforwardly allows simulations on Open Street Maps
5. Allows both traditional discrete-time ABM simulations as well as continuous time "event queue based" ABM simulations.

More information and an extensive list of features can be found in the documentation, which you can either find [online](https://juliadynamics.github.io/Agents.jl/stable/) or build locally by running the `docs/make.jl` file.

## Citation

If you use this package in a publication, or simply want to refer to it, please cite the paper below:

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
