```
select125(x)
```

Select elements of the collection x by index according to 1-2-5 scheme

#### Examples:

```@docs
x = [1,2,4,6,8,10,13,16,18,20,40,60,80,100]
select125(x)
 [2, 6, 10, 16, 20, 60, 100]

x = string.(x)
select125(x)
 ["2", "6", "10", "16", "20", "60", "100"]

x = 1:100
select125(x)
 [20, 40, 60, 80, 100]
```
