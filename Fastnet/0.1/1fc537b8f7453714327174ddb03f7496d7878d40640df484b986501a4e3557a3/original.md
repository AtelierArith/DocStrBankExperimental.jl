```
savelinklist(net,filename)
```

Save network link list of network *net* to file *filename*.

The file is written in text mode. Each line that is written correosponds to  one link. The lines have the form 

```
LINKID SOURCE DESTINATION
```

Where LINKID is the respective link, SOURCE is the node id of the source node and DESTINATION  is the node id  of the destination node. The elemnts are separated by space. The line is ended by a line feed '\n'.

See also [linklist](#Fastnet.linklist) 
