```
simulate_AR1(p::Int, a=1, b=1, tol=1e-3, max_corr=1, rho=nothing)
```

`p`次元の相関行列をAR(1)ガウス過程のために生成します。ここで、連続する相関はBeta(`a`,`b`)から独立に引き出されます。`rho`が指定されている場合、プロセスは相関`rho`を持つ定常状態になります。

# ソース

https://github.com/amspector100/knockpy/blob/20eddb3eb60e0e82b206ec989cb936e3c3ee7939/knockpy/dgp.py#L61
