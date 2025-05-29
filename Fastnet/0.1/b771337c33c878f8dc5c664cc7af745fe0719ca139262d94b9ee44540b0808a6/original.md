```
healthcheck(net)
```

Perform an internal consistencey check on a FastNet *net*.

To achieve the desired performance Fastnet engages in a certain amount of double bookeeping. In an ideal world the FastNet structures should always stay internally consistent. However, inconsistencies could arise from a number of sources including software bugs, CPU and memeory  errors. This function checks the internal data stored in FastNet for consistency to make sure  that everything is alright. 

The return value is true if all chacks have been passed, false otherwise. 

See also [link](#Fastnet.link)

# Examples

```jldoctest
julia> using Fastnet

julia> net=FastNet(100,200,10,[])
Network of 0 nodes and 0 links

julia> healthcheck(net);
  Checking repository consistency ... OK
  Checking node accounting ... OK
  Checking link accounting ... OK
  Checking endpoint consistency ... OK
  Checking node stateification ... OK
  Checking link stateification ... OK
```
