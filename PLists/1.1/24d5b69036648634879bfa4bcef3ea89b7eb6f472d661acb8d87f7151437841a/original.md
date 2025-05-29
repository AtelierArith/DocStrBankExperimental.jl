```
PLists
```

This is a simple example of how to read an XML file. 

```julia-repl
julia> doc = readxml("examples/note.xml");
julia> r = root(doc);
julia> ns = nodes(r);
```

You can use an array or dictionary interface to work with child nodes or attribute nodes.

To read a NeXT or Apple style property list:

```julia-repl
julia> dict = readplist("test/example.plist")
```

This gives you a regular dictionary you can work with.
