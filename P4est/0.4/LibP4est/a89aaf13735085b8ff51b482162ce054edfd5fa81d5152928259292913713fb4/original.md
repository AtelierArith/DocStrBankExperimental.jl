Store a parallel numbering of Lobatto points of a given degree > 0.

Each element has degree+1 nodes per edge and vnodes = (degree+1)^3 nodes per volume. element_nodes is of dimension vnodes * num_local_elements and lists the nodes of each element in lexicographic yx-order (x varies fastest); element_nodes indexes into the set of local nodes, layed out as follows: local nodes = [<––-owned_count––->|<––-nonlocal_nodes––->] = [<––––––––num_local_nodes––––––––->] nonlocal_nodes contains the globally unique numbers for independent nodes that are owned by other processes; for local nodes, the globally unique numbers are given by i + global_offset, where i is the local number. Hanging nodes are always local and don't have a global number. They index the geometrically corresponding independent nodes of a neighbor.

Whether nodes are hanging or not is decided based on the element faces and edges. This information is encoded in face_code with one int16_t per element. If no faces or edges are hanging, the value is zero, otherwise the face_code is interpreted by p8est_lnodes_decode.

Independent nodes can be shared by multiple MPI ranks. The owner rank of a node is the one from the lowest numbered element on the lowest numbered octree *touching* the node.

What is meant by *touching*? A quadrant is said to touch all faces/edges/corners that are incident on it, and by extension all nodes that are contained in those faces/edges/corners.

X +–––––-+ x |\ \ x | \ \ . x | \ \ x X | +–––––-+ +––-+ . . | | | |\ \ X o + | | | +––-+ o . \ | p | + | q | o \ | | \| | o \| | +––-+ O +–––––-+

In this example degree = 3. There are 4 nodes that live on the face between q and p, two on each edge and one at each corner of that face. The face is incident on q, so q owns the nodes marked '.' on the face (provided q is from a lower tree or has a lower index than p). The bottom and front edges are incident on q, so q owns its nodes marked 'o' as well. The front lower corner is incident on q, so q owns its node 'O' as well. The other edges and corners are not incident on q, so q cannot own their nodes, marked 'x' and 'X'.

global_owned_count contains the number of independent nodes owned by each process.

The sharers array contains items of type [`p8est_lnodes_rank_t`](@ref) that hold the ranks that own or share independent local nodes. If there are no shared nodes on this processor, it is empty. Otherwise, it is sorted by rank and the current process is included.

degree < 0 indicates that the lnodes data structure is being used to number the quadrant boundary object (faces, edge and corners) rather than the $C^0$ Lobatto nodes:

if degree == -1, then one node is assigned per face, and no nodes are assigned per volume, per edge, or per corner: this numbering can be used for low-order Raviart-Thomas elements. In this case, vnodes == 6, and the nodes are listed in face-order.

if degree == -2, then one node is assigned per face and per edge and no nodes are assigned per volume or per corner. In this case, vnodes == 18, and the nodes are listed in face-order, followed by edge-order.

if degree == -3, then one node is assigned per face, per edge and per corner and no nodes are assigned per volume. In this case, vnodes == 26, and the nodes are listed in face-order, followed by edge-order, followed by corner-order.
