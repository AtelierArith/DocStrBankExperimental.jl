checks bus types are suitable for a power flow study, if not, fixes them.

the primary checks are that all type 2 buses (i.e., PV) have a connected and active generator and there is a single type 3 bus (i.e., slack bus) with an active connected generator.

assumes that the network is a single connected component
