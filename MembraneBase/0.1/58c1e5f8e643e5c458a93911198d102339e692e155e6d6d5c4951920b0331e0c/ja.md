```
isotherm_dataset(x::Matrix, y::Matrix, component::Int)
```

は、2つの等温成分をベクトルステップの形式[(type*x, type*y)...]に変換します。多成分等温の場合、形式はdataset[step] = [[xcomp1, xcomp2, ...], [ycomp1, ycomp2, ...]]です。例えば、`mydataset = Isotherm.dataset(myisotherm.partial_pressures, myisotherm.concentrations)`は、次の形式のベクトルのベクトルを返します: myset[1] = [[(成分1の圧力), (成分2の圧力), ...], [(成分1の濃度), (成分2の濃度), ...]]
