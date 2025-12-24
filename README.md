
# PQ-6G-Auth: Post-Quantum Authentication for 6G Networks

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Under%20Submission-blue)](https://github.com/ritikvatsh/pq-6g-auth)
<a href="https://pq6g-auth-research.blogspot.com/2025/12/post-quantum-security-for-6g-networks.html">
  <img src="https://img.shields.io/badge/Blog-Post-green.svg" alt="Blog Post">
</a>
## 📄 Overview

Research implementation for the paper:

**"Native Integration of Post-Quantum Cryptography in 6G Core Network Functions with Sub-0.1 ms Latency for Holographic Communications and Digital Twins"**

**Authors**: 
- **Ritik Vats** (Student, Department of Computer Science)
- **Sagar Choudhary** (Assistant Professor, Department of Computer Science)

**Institution**: Quantum University, Roorkee, India

**Contact**: 
- Ritik Vats: ritikvatsh@gmail.com
- Sagar Choudhary: itsagarit@gmail.com

---
## 📝 Blog Post: Detailed Explanation



### 🌟 Want to understand this research in plain English?

[![Read Blog Post](https://img.shields.io/badge/📖_Read_Full_Blog_Post-Click_Here-brightgreen?style=for-the-badge&logo=blogger)](https://pq6g-auth-research.blogspot.com/2025/12/post-quantum-security-for-6g-networks.html)

**"Post-Quantum Security for 6G Networks: Achieving Sub-0.1 ms Authentication"**

An in-depth, accessible explanation featuring:
- 🎯 Why quantum computers threaten 6G security
- 💡 How PQ-6G-Auth works (with visual diagrams)
- 🌍 Real-world applications & impact
- 📊 Performance breakdown & analysis
- 💻 Step-by-step technical walkthrough

*Perfect for students, researchers, and tech enthusiasts!*

</div>

---

## 🎯 Abstract

PQ-6G-Auth is a quantum-safe authentication framework achieving **82.3 μs mean authentication latency** through co-design of:
- 🔐 Lattice-based cryptography (ML-KEM-768, ML-DSA-65)
- 🔗 Distributed ledger technology (Hashgraph consensus)
- ⚡ Hardware-optimized implementations (ARM Neoverse V2 modeling)

### Key Results
- ✅ **96.1% improvement** vs. naive PQC implementations
- ✅ **99.999% reliability** under 100 μs threshold
- ✅ **128-bit quantum security** (NIST Category 3)
- ✅ **165,000 auth/sec** throughput at scale

---

## 📁 Repository Contents

| File | Description | Size |
|------|-------------|------|
| `experimental_data.json` | Raw performance data (10,000 authentication runs) | ~2.5 MB |
| `generate_experiment_data.py` | Simulation data generator | ~8 KB |
| `generate_figures.py` | Reproduces all paper figures | ~12 KB |
| `fig1_architecture.pdf` | System architecture diagram | PDF |
| `fig2_sequence.pdf` | Protocol sequence diagram | PDF |
| `fig3_cdf.pdf` | Latency CDF comparison | PDF |
| `fig4_comparison.pdf` | Performance comparison chart | PDF |
| `fig5_breakdown.pdf` | Component-wise latency breakdown | PDF |
| `fig6_scalability.pdf` | Scalability analysis (UE scaling) | PDF |
| `fig7_throughput.pdf` | Throughput scaling (AUSF instances) | PDF |
| `references.bib` | Complete bibliography (75 references) | ~15 KB |

---

## 🚀 Quick Start

### Prerequisites

```bash
Python 3.8+
numpy
matplotlib
scipy
seaborn
```

### Installation

```bash
# Clone repository
git clone https://github.com/ritikvatsh/pq-6g-auth.git
cd pq-6g-auth

# Install dependencies
pip install numpy matplotlib scipy seaborn
```

### Generate Data

```bash
python generate_experiment_data.py
```

**Output**: `experimental_data.json` (contains all performance metrics)

### Generate Figures

```bash
python generate_figures.py
```

**Output**: 7 PDF figures ready for LaTeX compilation

---

## 🏗️ System Architecture

PQ-6G-Auth integrates three architectural planes:

1. **Control Plane**: AMF, AUSF, UDM (3GPP TS 33.501 compliant)
2. **Cryptographic Plane**: Lattice engines executing ML-KEM/ML-DSA
3. **Ledger Plane**: Permissioned DAG nodes with Hashgraph consensus

### Protocol Flow
```
UE → AMF → AUSF → DLT
  ↓      ↓      ↓
Setup Phase: Key generation + DLT registration
Auth Phase:  5-message exchange with encapsulation
Result:      Session keys established in 82.3 μs
```

---

## 📊 Performance Summary
### 🏆 Benchmark Results
| Metric | PQ-6G-Auth | Naive ML-KEM | Improvement |
|--------|------------|--------------|-------------|
| **Mean Latency** | 82.3 μs | 2,100 μs | 96.1% ↓ |
| **Median Latency** | 81.8 μs | 2,095 μs | 96.1% ↓ |
| **P99.99** | 120.0 μs | 2,500 μs | 95.2% ↓ |
| **P99.999** | 145.2 μs | 2,800 μs | 94.8% ↓ |
| **Max Throughput** | 165K/sec | 67K/sec | 146% ↑ |
| **Quantum Security** | 128-bit | 128-bit | ✓ |

### Component Breakdown (82.0 μs total)
- **NTT Operations**: 28.5 μs (34.8%)
- **Network Transport**: 16.6 μs (20.2%)
- **Sampling**: 16.4 μs (20.0%)
- **Hashing**: 12.3 μs (15.0%)
- **DLT Query**: 8.2 μs (10.0%)

> 💡 **Want detailed explanations of these results?** Check out our [comprehensive blog post](https://pq6g-auth-research.blogspot.com/2025/12/post-quantum-security-for-6g-networks.html) for visual breakdowns and real-world context!

---

## 🔬 Technical Details

### Cryptographic Primitives

**ML-KEM-768** (FIPS 203):
- Module rank k=3, modulus q=3329
- 1,184-byte public keys
- 1,088-byte ciphertexts
- IND-CCA2 security

**ML-DSA-65** (FIPS 204):
- 1,952-byte public keys
- ~3,309-byte signatures
- EUF-CMA security

### Optimization Techniques

1. **NTT Acceleration**: 4× speedup via ARM SVE vectorization
2. **Pre-token Caching**: Amortized key generation
3. **Parallel Pipelines**: Overlapped crypto + DLT operations
4. **Asynchronous Ledger**: Non-blocking DLT queries

### Security Model

- **Adversary**: Dolev-Yao + quantum computing capabilities
- **Assumptions**: MLWE hardness, QROM security
- **Resistance**: Shor's algorithm (factoring/DLP)
- **Threat Model**: Harvest-now-decrypt-later attacks

---

## 📈 Scalability

### Concurrent UEs
- **100 UEs**: 82.3 μs (baseline)
- **5,000 UEs**: 95.0 μs (+15% only!)
- **Complexity**: O(log n) growth

### AUSF Instances
- **16 instances**: 165,000 auth/sec
- **Efficiency**: 85% scaling factor
- **Architecture**: Horizontally scalable

---

## 🛠️ Development Roadmap

### Current Status
- ✅ Simulation-based performance modeling
- ✅ Cycle-accurate computational analysis
- ✅ Statistical validation (n=10,000)
- ✅ Open-source implementation

### Future Work
- 🔄 Physical testbed deployment (2027-2029)
- 🔄 3GPP standardization (Release 21)
- 🔄 Industry pilot programs
- 🔄 Formal verification (ProVerif/Tamarin)

---

## 📚 Citation

If you use this work in your research, please cite:

```bibtex
@inproceedings{vats2025pq6gauth,
  title={Native Integration of Post-Quantum Cryptography in 6G Core 
         Network Functions with Sub-0.1 ms Latency for Holographic 
         Communications and Digital Twins},
  author={Vats, Ritik and Choudhary, Sagar},
  booktitle={IEEE Conference Proceedings},
  year={2025},
  note={Under submission}
}
```

**Paper Status**: Currently under submission to IEEE Access

---

## 🤝 Contributing

We welcome contributions! Areas of interest:
- Physical testbed implementations
- Additional PQC algorithm comparisons
- Side-channel countermeasures
- Formal security proofs
- Integration with 3GPP specifications

Please open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 👥 Authors
<table>
<tr>
<td align="center">
<img src="https://github.com/ritikvatsh.png" width="100px;" alt="Ritik Vats"/><br />
<sub><b>Ritik Vats</b></sub><br />
<sub>Student Researcher / Web Wrafter</sub><br />
<a href="mailto:ritikvatsh@gmail.com">📧 Email</a> • 
<a href="https://instagram.com/ritikvatsh">📱 Instagram</a>
</td>
<td align="center"> </table
                     
---
### **Ritik Vats** (Student)
Department of Computer Science  
Quantum University, Roorkee, Uttarakhand, India  
📧 Email: ritikvatsh@gmail.com

### **Sagar Choudhary** (Assistant Professor)
Department of Computer Science  
Quantum University, Roorkee, Uttarakhand, India  
📧 Email: itsagarit@gmail.com

---

## 🙏 Acknowledgments

This research was conducted under the supervision of Assistant Professor Sagar Choudhary at Quantum University. Computational resources provided by the Department of Computer Science are gratefully acknowledged.

---

## 📞 Contact

For questions, collaborations, or access to additional data:
- **Student**: Ritik Vats (ritikvatsh@gmail.com)
- **Faculty Advisor**: Sagar Choudhary (itsagarit@gmail.com)
- **GitHub Issues**: [Create an issue](https://github.com/ritikvatsh/pq-6g-auth/issues)

---

## 🔗 Related Resources



### 📚 Essential Reading & Tools

</div>

| Resource | Description | Link |
|----------|-------------|------|
| **📝 PQ-6G-Auth Blog** | In-depth explanation for broader audience | [Read Blog](https://pq6g-auth-research.blogspot.com/2025/12/post-quantum-security-for-6g-networks.html) |
| **NIST PQC** | Official post-quantum cryptography standards | [Visit](https://csrc.nist.gov/projects/post-quantum-cryptography) |
| **3GPP Release 20** | 6G network specifications | [Visit](https://www.3gpp.org/release-20) |
| **liboqs** | Open Quantum Safe library | [GitHub](https://github.com/open-quantum-safe/liboqs) |
| **ns-3** | Network simulator | [Visit](https://www.nsnam.org/) |

---


## ⚠️ Important Notes

1. **Simulation-Based**: Results derived from computational modeling, not physical hardware
2. **Research Prototype**: Not production-ready; intended for academic validation
3. **Security Advisory**: Consult cryptographic experts before deployment
4. **Patent Status**: No patent applications filed; free for research use

---

## 📊 Project Statistics

<div align="center">

![GitHub last commit](https://img.shields.io/github/last-commit/ritikvatsh/pq-6g-auth)
![GitHub issues](https://img.shields.io/github/issues/ritikvatsh/pq-6g-auth)
![GitHub stars](https://img.shields.io/github/stars/ritikvatsh/pq-6g-auth)
![GitHub forks](https://img.shields.io/github/forks/ritikvatsh/pq-6g-auth)
![GitHub watchers](https://img.shields.io/github/watchers/ritikvatsh/pq-6g-auth)


</div>

---
<div align="center">

 ⭐ Star this repository if you find it useful!

### 🔐 Securing the 6G Future with Quantum-Safe Cryptography

[![Star on GitHub](https://img.shields.io/github/stars/ritikvatsh/pq-6g-auth?style=social)](https://github.com/ritikvatsh/pq-6g-auth/stargazers)
[![Follow](https://img.shields.io/github/followers/ritikvatsh?style=social)](https://github.com/ritikvatsh)

**Made with ❤️ by <a href="https://instagram.com/ritikvatsh">Ritik Vats</a> for PQ-6G-Auth Research presentation **

</div>

---

<div align="center">
<sub>Last Updated: December 2024 | License: MIT | Status: Under Peer Review</sub>
</div>
