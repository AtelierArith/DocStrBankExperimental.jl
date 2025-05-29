Collapse unnecessary assignment nodes, rewriting all affected nodes. Example:

```
tmp1 = x * y
z = tmp1
```

will be rewritten to

```
z = x * y
```
