```
mesh3d(x,y,z)
mesh3d(x,y,z; connections)
```

3Dメッシュをプロットします。Plotlyでは、三角形はconnections引数を使用して指定できます。

# 例

```Julia
x=[0, 1, 2, 0]
y=[0, 0, 1, 2]
z=[0, 2, 0, 1]

i=[0, 0, 0, 1]
j=[1, 2, 3, 2]
k=[2, 3, 1, 3]

plot(x,y,z,seriestype=:mesh3d;connections=(i,j,k))
```
