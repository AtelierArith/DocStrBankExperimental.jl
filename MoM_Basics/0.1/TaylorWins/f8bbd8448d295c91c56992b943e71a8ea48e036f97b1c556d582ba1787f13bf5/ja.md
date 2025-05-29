```
taylorwin(L::IT, nbar = 4, sll = -30) where {IT<:Integer}
```

TAYLORWIN   テイラーウィンドウ。

TAYLORWIN(N) は、Nポイントのテイラーウィンドウを列ベクトルで返します。

TAYLORWIN(N,nbar) は、nbarが主ローブに隣接するほぼ一定レベルのサイドローブを持つNポイントのテイラーウィンドウを返します。nbarは1以上の整数でなければなりません。

TAYLORWIN(N,nbar,sll) は、sllが主ローブのピークに対してdBで相対的な最大サイドローブレベルを持つNポイントのテイラーウィンドウを返します。sllは負の値でなければなりません。例えば、-30 dBです。

nbarはnbar >= 2*A^2+0.5を満たす必要があります。ここで、Aはacosh(10^(-sll/20))/piに等しいです。そうでない場合、指定されたサイドローブレベルは保証されません。nbarが指定されていない場合、デフォルトは4です。sllは指定されていない場合、デフォルトは-30 dBです。

EXAMPLE この例では、主ローブに隣接する4つのサイドローブを持ち、ほぼ一定レベルの64ポイントのテイラーウィンドウを生成し、主ローブのピークに対して-35 dBのピークサイドローブレベルを持ちます。

w = taylorwin(64,5,-35); wvtool(w);

CHEBWINも参照してください。

Copyright 2005-2018 The MathWorks, Inc.

References:     [1] Carrara, Walter G., Ronald M. Majewski, and Ron S. Goodman,         Spotlight Synthetic Aperture Radar: Signal Processing Algorithms,         Artech House, October 1, 1995.     [2] Brookner, Eli, Practical Phased Array Antenna Systems,         Artech House, Inc., 1991, pg. 2-51.
