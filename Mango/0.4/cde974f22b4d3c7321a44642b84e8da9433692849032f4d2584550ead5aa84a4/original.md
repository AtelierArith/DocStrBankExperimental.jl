Default Implementation Communication Sim.

Implements a default delay which determines the delay of all messages if not specified in  `delay_s_directed_edge_dict`. The dict can contain a mapping (aid*sender, aid*receiver) -> delay, such that the delay is specified for every link between agents.
