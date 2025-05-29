```
colnames(itr)
```

Returns the names of the "columns" in `itr`.

# Examples:

```
colnames(1:3)
colnames(Columns([1,2,3], [3,4,5]))
colnames(table([1,2,3], [3,4,5]))
colnames(Columns(x=[1,2,3], y=[3,4,5]))
colnames(table([1,2,3], [3,4,5], names=[:x,:y]))
colnames(ndsparse(Columns(x=[1,2,3]), Columns(y=[3,4,5])))
colnames(ndsparse(Columns(x=[1,2,3]), [3,4,5]))
colnames(ndsparse(Columns(x=[1,2,3]), [3,4,5]))
colnames(ndsparse(Columns([1,2,3], [4,5,6]), Columns(x=[6,7,8])))
colnames(ndsparse(Columns(x=[1,2,3]), Columns([3,4,5],[6,7,8])))
```
