```
ps(c::Container)
```

Get a list of agents running in a container. The list contains tuples of agent name and agent type. The agent type may be an empty string for agents running in remote containers, if the containers do not support type query.
