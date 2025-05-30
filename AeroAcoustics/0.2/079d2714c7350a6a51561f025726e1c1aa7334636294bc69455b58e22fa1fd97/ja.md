```
cleanSC(E[;maxiter=50,ϕ=0.5,stopn=10,peak_removal=false,trust_region=nothing])
```

CLEAN-SCアルゴリズムは、最大反復回数`maxiter`（デフォルト50）およびループゲイン`ϕ`（デフォルト0.5）をオプションで設定し、ソースの特定と定量化を行います。さらに、停止基準`max_peak[i] > max_peak[i-stopn]`は、パラメータ`stopn`を使用して設定できます。ダーティマップ内のピークソースの減算は、`peak_removal=true/false`を使用してサポートされており、`trust_region`の外にあるピークソースを削除します。制限は`[xmin,xmax,ymin,ymax]`として与えられ、例えば`trust_region=[-0.75;1.5;-1.0;1.0]`のようになります。

# 参考文献:

  * Sijtsma, P. (2007). CLEAN based on spatial source coherence. International Journal of Aeroacoustics, 6(4), 357–374.

インスピレーションを受けたリンク: https://github.com/acoular/acoular/blob/66cba3cffb3bc72602c869f99347be76798f4ac1/acoular/fbeamform.py#L1496
