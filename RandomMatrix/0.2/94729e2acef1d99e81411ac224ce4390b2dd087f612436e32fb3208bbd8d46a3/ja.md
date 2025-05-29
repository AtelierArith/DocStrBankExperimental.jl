```julia
# 例

# ランダムエルミート行列の解決子はおおよそ対角的であり、 
# https://arxiv.org/pdf/1903.10060.pdf のセクション3を参照してください
 normview(resolvent(randHermitian(1000,norm=true))(0.5+0.1im))
```
