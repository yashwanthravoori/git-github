# git-github
import random

class Node:
    def __init__(self, id):
        self.id = id
        self.neighbors = set()

    def add_neighbor(self, node):
        self.neighbors.add(node)
        node.neighbors.add(self)

    def remove_neighbor(self, node):
        self.neighbors.remove(node)
        node.neighbors.remove(self)

    def __repr__(self):
        return f"Node {self.id}"

class Network:
    def __init__(self, num_nodes):
        self.nodes = []
        for i in range(num_nodes):
            self.nodes.append(Node(i))

    def connect_nodes(self, node1, node2):
        self.nodes[node1].add_neighbor(self.nodes[node2])

    def disconnect_nodes(self, node1, node2):
        self.nodes[node1].remove_neighbor(self.nodes[node2])

    def get_random_node(self):
        return random.choice(self.nodes)

    def __repr__(self):
        return f"Network with {len(self.nodes)} nodes"

# Create a network with 10 nodes
network = Network(10)

# Connect some nodes randomly
network.connect_nodes(0, 1)
network.connect_nodes(2, 3)
network.connect_nodes(4, 5)
network.connect_nodes(6, 7)
network.connect_nodes(8, 9)

# Disconnect some nodes randomly
network.disconnect_nodes(1, 2)
network.disconnect_nodes(4, 6)
network.disconnect_nodes(7, 9)

# Print the network's nodes and their neighbors
for node in network.nodes:
    print(f"{node}: {node.neighbors}")
