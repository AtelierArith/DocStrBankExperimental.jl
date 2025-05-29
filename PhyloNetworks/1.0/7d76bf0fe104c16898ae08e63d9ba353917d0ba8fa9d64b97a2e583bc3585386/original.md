```
writemultinewick(nets, file_name; append=false)
writemultinewick(nets, IO)
```

Write an array of networks in parenthetical extended Newick format, one network per line. Use the option append=true to append to the file. Otherwise, the default is to create a new file or overwrite it, if it already existed. Each network is written with `writenewick`.

# Examples

```julia
julia> net = [readnewick("(D,((A,(B)#H7:::0.864):2.069,(F,E):3.423):0.265,(C,#H7:::0.1361111):10);"),
              readnewick("(A,(B,C));"),readnewick("(E,F);"),readnewick("(G,H,F);")];

julia> writemultinewick(net, "fournets.net") # to (over)write to file "fournets.net"
julia> writemultinewick(net, "fournets.net", append=true) # to append to this file
julia> writemultinewick(net, stdout)         # to write to the screen (standard out)
(D,((A,(B)#H7:::0.864):2.069,(F,E):3.423):0.265,(C,#H7:::0.1361111):10.0);
(A,(B,C));
(E,F);
(G,H,F);
```
