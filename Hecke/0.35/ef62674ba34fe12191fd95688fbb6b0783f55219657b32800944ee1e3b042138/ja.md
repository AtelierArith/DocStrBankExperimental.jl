```
theta(z::Vector{AcbFieldElem},  tau::AcbMatrix}; char::Vector{Vector{Int}},
dz::Vector{Vector{Int}}, dtau::Vector{Vector{Int}}, prec::Int) -> AcbFieldElem
```

tauとzのtheta(tau, z)の値を、精度をprec、zの精度、tauの精度の最小値で計算します。オプションとして、dzを標準基底の要素のリストに設定することで、指定された方向で点zにおける特性charを持つTheta関数の導関数を計算できます。（例えば、genus 3の場合、dz = [[1,0,0], [0,0,1]]と設定すると、dtheta(z, tau)/(dx1 dx3)が計算されます）。同様に、dtauを整数のタプルのリストに設定することで、周期行列tauに関しての導関数を取ることができます。（例えば、dtau = [[1,2]]と設定すると、dtheta(z, tau)/dtau_{1,3}が計算されます）
