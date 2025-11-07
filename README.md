# Sistema de Otimização de Rotas de Entrega

Projeto Spring Boot com algoritmos de otimização de rotas para logística e entregas.

## Estrutura do Projeto

```
src/main/java/com/example/routing/
├── models/
│   ├── Grafo.java          # Estrutura de dados para representar grafos
│   ├── Cliente.java        # Modelo de cliente com janelas de tempo
│   └── Rota.java           # Modelo de rota com caminho e métricas
├── algorithms/
│   ├── Dijkstra.java       # Algoritmo de menor caminho
│   ├── TSP.java            # Problema do Caixeiro Viajante
│   ├── EntregaComTempo.java # Roteamento com janelas de tempo
│   └── VRP.java            # Problema de Roteamento de Veículos
├── service/
│   └── RotasService.java   # Service com os 4 problemas de roteamento
├── utils/
│   ├── GrafoVisualizer.java # Visualização de grafos e rotas
│   └── TimeUtils.java       # Utilitários de tempo
└── Main.java               # Classe principal Spring Boot
```

## Requisitos

- Java 17+
- Maven 3.6+

## Como Executar

```bash
mvn spring-boot:run
```

O sistema executará automaticamente os 4 problemas de roteamento:

## Problemas Implementados

### 1. Caminho Mais Curto (Dijkstra)
Encontra o menor caminho entre dois pontos em um grafo ponderado.
- Algoritmo: Dijkstra
- Uso: Entrega única, rota mais rápida

### 2. Caixeiro Viajante (TSP)
Encontra a rota mais curta que visita todos os pontos e retorna ao início.
- Algoritmos: Vizinho Mais Próximo (heurística) e Força Bruta (ótimo)
- Uso: Múltiplas entregas, um único veículo

### 3. Entregas com Janelas de Tempo
Planeja rotas respeitando horários de atendimento dos clientes.
- Considera: Tempo de viagem, janelas de tempo, tempo de serviço
- Uso: Entregas com horários agendados

### 4. Roteamento de Veículos (VRP)
Otimiza rotas para múltiplos veículos com restrições de capacidade.
- Considera: Capacidade dos veículos, demanda dos clientes
- Uso: Frota de veículos, entregas com peso/volume

## Exemplo de Saída

```
======================================================================
SISTEMA DE OTIMIZAÇÃO DE ROTAS DE ENTREGA
======================================================================

PROBLEMA 1: CAMINHO MAIS CURTO (Dijkstra)
Rota: A → C → E → F
Distância total: 14.0 km

PROBLEMA 2: CAIXEIRO VIAJANTE (TSP)
Vizinho Mais Próximo: 125.0 km
Solução Ótima: 120.0 km

PROBLEMA 3: ENTREGAS COM JANELAS DE TEMPO
✅ Rota VIÁVEL
Tempo total: 125 minutos

PROBLEMA 4: ROTEAMENTO DE VEÍCULOS (VRP)
🚚 Veículo 1: CD → C1 → C2 → CD (75kg)
🚚 Veículo 2: CD → C3 → C4 → CD (85kg)
```
