```
GraphShortestPathEnv([rng]; n=10, sparsity=0.1, max_steps=10)
```

Quoted **A.3** in the the paper [Decision Transformer: Reinforcement Learning via Sequence Modeling](https://arxiv.org/abs/2106.01345).

> We give details of the illustrative example discussed in the introduction. The task is to find theshortest path on a fixed directed graph, which can be formulated as an MDP where reward is0whenthe agent is at the goal node and−1otherwise.  The observation is the integer index of the graphnode the agent is in. The action is the integer index of the graph node to move to next. The transitiondynamics transport the agent to the action’s node index if there is an edge in the graph, while theagent remains at the past node otherwise. The returns-to-go in this problem correspond to negativepath lengths and maximizing them corresponds to generating shortest paths.

