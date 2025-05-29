Store a parallel numbering of Lobatto points of a given degree > 0.

Each element has degree+1 nodes per face and vnodes = (degree+1)^2 nodes per volume. num_local_elements is the number of local quadrants in the `p4est`. element_nodes is of dimension vnodes * num_local_elements and lists the nodes of each element in lexicographic yx-order (x varies fastest); so for degree == 2, this is the layout of nodes:

f_3 c_2 c_3 6–-7–-8 | | f_0 3 4 5 f_1 | | 0–-1–-2 c_0 c_1 f_2

element_nodes indexes into the set of local nodes, layed out as follows: local nodes = [<––-owned_count––->|<––-nonlocal_nodes––->] = [<––––––––num_local_nodes––––––––->] nonlocal_nodes contains the globally unique numbers for independent nodes that are owned by other processes; for local nodes, the globally unique numbers are given by i + global_offset, where i is the local number. Hanging nodes are always local and don't have a global number. They index the geometrically corresponding independent nodes of a neighbor.

Whether nodes are hanging or not is decided based on the element faces. This information is encoded in face_code with one int8_t per element. If no faces are hanging, the value is zero, otherwise the face_code is interpreted by p4est_lnodes_decode.

Independent nodes can be shared by multiple MPI ranks. The owner rank of a node is the one from the lowest numbered element on the lowest numbered octree *touching* the node.

What is meant by *touching*? A quadrant is said to touch all faces/corners that are incident on it, and by extension all nodes that are contained in those faces/corners.

X +–––––-+ o | | o | | +––-+ o | p | | q | o | | | | o | | +––-+ O +–––––-+

In this example degree = 6. There are 5 nodes that live on the face between q and p, and one at each corner of that face. The face is incident on q, so q owns the nodes on the face (provided q is from a lower tree or has a lower index than p). The lower corner is incident on q, so q owns it as well. The upper corner is not incident on q, so q cannot own it.

global_owned_count contains the number of independent nodes owned by each process.

The sharers array contains items of type [`p4est_lnodes_rank_t`](@ref) that hold the ranks that own or share independent local nodes. If there are no shared nodes on this processor, it is empty. Otherwise, it is sorted by rank and the current process is included.

degree < 0 indicates that the lnodes data structure is being used to number the quadrant boundary object (faces and corners) rather than the $C^0$ Lobatto nodes:

if degree == -1, then one node is assigned per face, and no nodes are assigned per volume or per corner: this numbering can be used for low-order Raviart-Thomas elements. In this case, vnodes == 4, and the nodes are listed in face-order:

f_3 c_2 c_3 +–-3–-+ | | f_0 0 1 f_1 | | +–-2–-+ c_0 c_1 f_2

if degree == -2, then one node is assigned per face and per corner and no nodes are assigned per volume. In this case, vnodes == 8, and the nodes are listed in face-order, followed by corner-order:

f_3 c_2 c_3 6–-3–-7 | | f_0 0 1 f_1 | | 4–-2–-5 c_0 c_1 f_2
