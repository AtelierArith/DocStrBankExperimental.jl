```
likelihoodof(k::AbstractTransitionKernel, x; constraints...)
likelihoodof(k::AbstractTransitionKernel, x, constraints::NamedTuple)
```

尤度は*測度*ではありません。むしろ、尤度は測度に作用し、「点ごとの積」`⊙`を通じて別の測度を生成します。
