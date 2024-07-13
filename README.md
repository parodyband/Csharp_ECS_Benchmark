``` ini

BenchmarkDotNet=v0.13.5, OS=Windows 11 (10.0.22631.3880)
AMD Ryzen 9 5950X, 1 CPU, 32 logical and 16 physical cores
.NET SDK=7.0.306
  [Host]     : .NET 7.0.9 (7.0.923.32018), X64 RyuJIT AVX2
  DefaultJob : .NET 7.0.9 (7.0.923.32018), X64 RyuJIT AVX2


```
|             Method |     Type |        Mean |     Error |     StdDev |      Median | BranchInstructions/Op | CacheMisses/Op | BranchMispredictions/Op |   Gen0 | Allocated |
|------------------- |--------- |------------:|----------:|-----------:|------------:|----------------------:|---------------:|------------------------:|-------:|----------:|
|    **UpdatePositions** |      **SoA** | **1,637.55 μs** | **20.550 μs** |  **19.223 μs** | **1,635.93 μs** |             **4,941,427** |         **25,020** |                   **1,965** |      **-** |       **1 B** |
|  ApplyGlobalDamage |      SoA |   779.73 μs |  9.531 μs |   8.916 μs |   780.04 μs |             4,847,162 |         11,544 |                   1,732 |      - |       1 B |
|      ScaleEntities |      SoA |   896.70 μs | 17.670 μs |  17.354 μs |   891.94 μs |             3,895,213 |         10,986 |                   1,450 |      - |       1 B |
| CountAliveEntities |      SoA |   649.60 μs |  5.947 μs |   5.563 μs |   647.95 μs |             4,806,812 |         11,459 |                   1,629 |      - |       1 B |
|        ResetDamage |      SoA |   421.62 μs |  2.844 μs |   2.375 μs |   420.71 μs |             1,955,648 |          6,041 |                     700 |      - |         - |
|    **UpdatePositions** |      **AoS** | **2,317.84 μs** | **46.297 μs** | **127.514 μs** | **2,273.33 μs** |             **3,993,261** |         **43,695** |                   **1,939** |      **-** |       **2 B** |
|  ApplyGlobalDamage |      AoS | 2,043.16 μs | 40.799 μs | 113.730 μs | 1,988.61 μs |             4,960,033 |         48,396 |                   2,173 |      - |       2 B |
|      ScaleEntities |      AoS | 1,973.72 μs | 42.950 μs | 126.638 μs | 1,902.77 μs |             3,983,872 |         43,378 |                   1,847 |      - |       2 B |
| CountAliveEntities |      AoS | 1,599.33 μs | 31.977 μs |  43.770 μs | 1,581.46 μs |             4,940,983 |         46,851 |                   2,097 |      - |       1 B |
|        ResetDamage |      AoS |   423.12 μs |  4.443 μs |   4.156 μs |   420.64 μs |             1,955,746 |          5,215 |                     702 |      - |         - |
|    **UpdatePositions** | **SIMD_SoA** |   **189.62 μs** |  **3.689 μs** |   **3.788 μs** |   **189.51 μs** |             **1,138,385** |        **212,693** |                  **10,432** | **0.4883** |    **8607 B** |
|  ApplyGlobalDamage | SIMD_SoA |   157.54 μs |  2.846 μs |   2.662 μs |   157.56 μs |             1,123,061 |        122,268 |                   8,866 | 0.4883 |    9301 B |
|      ScaleEntities | SIMD_SoA |   158.97 μs |  2.991 μs |   2.938 μs |   158.87 μs |             1,121,012 |        124,985 |                   9,608 | 0.4883 |    8438 B |
| CountAliveEntities | SIMD_SoA |    83.29 μs |  1.855 μs |   5.441 μs |    81.55 μs |               976,616 |        125,354 |                   7,363 | 0.4883 |    9398 B |
|        ResetDamage | SIMD_SoA |    51.11 μs |  0.485 μs |   0.405 μs |    51.02 μs |               206,560 |         13,435 |                   3,270 | 0.4883 |    8307 B |

