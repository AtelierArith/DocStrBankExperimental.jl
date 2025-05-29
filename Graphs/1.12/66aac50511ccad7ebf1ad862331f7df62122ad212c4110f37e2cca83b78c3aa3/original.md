```
prufer_encode(g::SimpleGraph)
```

Given a tree (a connected minimal undirected graph) of size n⩾3, returns the unique Prüfer sequence associated with this tree. 

Each tree of size n ⩾ 2 is associated with a Prüfer sequence (a[1], ..., a[n-2]) with 1 ⩽ a[i] ⩽ n. The sequence is constructed recursively by the leaf removal algoritm. At step k, the leaf with smallest index is removed and its unique neighbor is added to the Prüfer sequence, giving a[k]. The Prüfer sequence of the tree with only one edge is the empty sequence. 

Ref: [Prüfer sequence on Wikipedia](https://en.wikipedia.org/wiki/Pr%C3%BCfer_sequence)
