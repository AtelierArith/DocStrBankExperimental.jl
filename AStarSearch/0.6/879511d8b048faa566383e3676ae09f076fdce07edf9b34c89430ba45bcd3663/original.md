astar(neighbours, start, goal;         heuristic=defaultheuristic, cost=defaultcost, isgoal=defaultisgoal, hashfn=hash, timeout=Inf, maxcost=Inf)

Execute the A* algorithm to get the best path from the start state to reach a goal condition. Only the first 3 arguments are mandatory, all the others are optional.

It returns a structure in which the `status` field is a Symbol that can be either:

  * `:success`: the algorithm found a path from start to goal
  * `:timeout`: the algorithm timed out, a partial path to the best state is returned in the `path` field
  * `:nopath`: the algorithm didn't find any path to a goal, the path to the best state is still returned

The other fields are:

  * `path`: an array of states from the start state to the goal or the best found state
  * `cost`: the cost of the returned path
  * `closedsetsize`: how many states the algorithm tested if they were a goal (size of the closed set)
  * `opensetsize`: how many states were still in the open set when the algorithm ended

# Arguments

  * `neighbours`: a function that takes a state and returns the neighbour states as an array (or iterable)
  * `start`: the starting state, the type of the state is completely unrestricted
  * `goal`: the goal state, the type is unrestricted, usually it's the same as the start
  * `heuristic`: a function that given a state and the goal returns an estimate of the cost to reach goal. This estimate should be optimistic if you want to be sure to get the best path. Notice that the best path could be very expensive to find, so if you want a good but not guaranteed optimal path, you could multiply your heuristic by a constant, the algorithm will usually be much faster
  * `cost`: a function that takes the current state and a neighbour and returns the cost to do that state transition. By default all transitions cost 1
  * `isgoal`: a function that takes a state and the goal and evaluates if the goal is reached (by default ==)
  * `hashfn`: a function that takes a state and returns a compact representation to use as dictionary key (usually one of UInt, Int, String), by default it is the base hash function. This is a very important field for composite states in order to avoid duplications. *WARNING* states with arrays as fields might return a different hash every time! If this is the case, please pass an hashfn that always returns the same value for the same state!
  * `timeout`: timeout in number of seconds after which the algorithm stops returning the best partial path to the state with the lowest heuristic, by default it is unrestricted. Please notice that the algorithm wil run *AT LEAST* the specified time.
  * `maxcost`: a maximum bound of the accumulated cost of the path, this can result in a :nopath result even if a path to the goal (with a greater cost) exists. By default it is Inf
  * `enable_closedset`: keep track of already visited nodes to avoid visiting them again, you might want to disable this if you know there isn't any loop in the state space graph (by default true)
