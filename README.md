# Two-Spin Heisenberg Hamiltonian Simulation using Qiskit

This project simulates the time evolution of the Heisenberg Hamiltonian for two spins on a quantum computer using Qiskit. It demonstrates how to approximate the unitary evolution operator  using **Trotterization** and compares simulation results across different quantum backends, including an ideal simulator, noisy simulator, and real IBM Quantum hardware (IBM Torino).

## The Physics

The Heisenberg Hamiltonian for two spins is given by:
$$H = J (X \otimes X + Y \otimes Y + Z \otimes Z)$$

To simulate the evolution $e^{-iHt}$, we use **Trotter-Suzuki decomposition**:
$$e^{-iH t} \approx \left( e^{-i J X \otimes X \Delta t} e^{-i J Y \otimes Y \Delta t} e^{-i J Z \otimes Z \Delta t} \right)^n$$
where $n$ is the number of Trotter steps and $\Delta t = t/n$.

## Features

* **Trotterization Circuit:** Implementation of a single Trotter step using standard quantum gates (`CX`, `RZ`, `RX`, `H`) to simulate $ZZ$, $YY$, and $XX$ interactions.
* **Multi-Backend Execution:** The simulation is structured to run on four different backends to compare performance:
    1.  **Ideal Simulator:** `AerSimulator` (Standard method).
    2.  **Tensor Network Simulator:** `AerSimulator` (Matrix Product State method) for efficient large-scale entanglement simulation.
    3.  **Noisy Simulation:** `FakeSherbrooke` provider to simulate the noise profile of a real IBM device before deployment.
    4.  **Real Hardware:** Execution on an operational IBM Quantum computer via `QiskitRuntimeService`.

## How to run?

* To run this notebook, you will need **Python** installed along with the following libraries:
  
  `pip install numpy matplotlib qiskit qiskit-aer qiskit-ibm-runtime`

Note: Access to real hardware requires valid IBM Quantum credentials configured in your environment.
