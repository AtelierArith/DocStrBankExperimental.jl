The Apogee to Apogee Path Sampler (AAPS) by Sherlock et al. (2022). 

AAPSは、No U-Turn Sampler (NUTS)のシンプルな代替手段です。NUTSと同様の目的を果たします：この手法は、標準HMCと比較して調整パラメータの選択に対して堅牢であるべきです。与えられた開始位置と運動量（x, v）に対して、AAPSは前方および後方の軌道を探索します。軌道はセグメントに分割され、セグメントはエネルギーランドスケープの-aplog pi(x)におけるアポジー（局所最大値）によって区切られます。調整パラメータ`K`は、探索するセグメントの数を定義します。
