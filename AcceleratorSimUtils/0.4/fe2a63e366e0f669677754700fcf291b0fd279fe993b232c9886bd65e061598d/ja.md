sincu(z, nd::Int = 0)

`nd = 0`の場合は、`sinc(z)`（`sin(z)/z`に等しい、ここにはπの因子はありません）を返し、`nd > 0`の場合は`nd`階の導関数を返します。

注意: 現在、`nd = 0`または`1`のみが実装されています。
