```
savenodeinfo(net,filename)
```

Save information about the nodes to file *filename*.

The file is written in text mode. Each line that is written correosponds to  one nodes. The lines have the form 

```
NODEID STATE INDEGREE OUTDEGREE IN-NEIGHBORS OUT-NEIGBORS
```

Where NODEID is the ID of the node, STATE is the state of the node, in degree is the number of links that have the node as the  destination, OUTDEGREE is the number of links that have the node as the source, IN-NEIGHBORS is a list of all nodes from which the  focal node receives an incoming link, OUTNEIGHBORS is a list of the IDs of all nodes from which the focal node casts an outgoing link.  All elements are separated by spaces The line is ended by a line feed '\n'.

See also [linklist](#Fastnet.linklist) 
