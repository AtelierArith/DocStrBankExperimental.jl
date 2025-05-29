```
shrink(method::TreeGP)
```

Returns an in-place expression mutation function that replaces a randomly chosen subtree with a randomly created terminal. This is a special case of subtree mutation where the replacement tree is a terminal. As with hoist mutation, it is motivated by the desire to reduce program size [^8].
