#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <locale.h>

// Definições de limite
#define MAX_LIVROS 100
#define MAX_BIBLIOTECARIOS 10
#define MAX_CLIENTES 100
#define MAX_EMPRESTIMOS 50
#define DIAS_LIMITE 7 // Limite de dias de empréstimo

/*Limpa a tela a cada necessidade de volta ao menu inicial*/
void limparTela() {
    #ifdef _WIN32
        system("cls");
    #else
        system("clear");
    #endif
}


// Estrutura de dados
typedef struct {
    int id;
    char nome[50];
} Bibliotecario;

typedef struct {
    int id;
    char nome[50];
} Cliente;

typedef struct {
    int id;
    char titulo[100];
    char autor[50];
    int disponivel;
} Livro;

typedef struct {
    int id;
    int idCliente;
    int idLivro;
    time_t dataRetirada;
    int diasEmprestimo;
} Emprestimo;

// Variáveis globais
Bibliotecario bibliotecarios[MAX_BIBLIOTECARIOS];
Cliente clientes[MAX_CLIENTES];
Livro livros[MAX_LIVROS];
Emprestimo emprestimos[MAX_EMPRESTIMOS];
int numBibliotecarios = 0;
int numClientes = 0;
int numLivros = 0;
int numEmprestimos = 0;
float valorMultaPorDia = 0.50; // Valor padrão de multa por dia
float valorEmprestimo = 5.00; // Valor padrão de empréstimo

// Funções CRUD para Bibliotecários
void criarBibliotecario() {
    if (numBibliotecarios < MAX_BIBLIOTECARIOS) {
        bibliotecarios[numBibliotecarios].id = numBibliotecarios + 1;
        printf("Nome do Bibliotecario: ");
        scanf(" %[^\n]", bibliotecarios[numBibliotecarios].nome);
        numBibliotecarios++;
        printf("\nBibliotecario(a) cadastrado(a) com sucesso!\n");
    } else {
        printf("Limite de bibliotecarios atingido.\n");
    }
    system("pause");
    limparTela();
}

void lerBibliotecarios() {
     limparTela();
    printf("Bibliotecarios cadastrados:\n");
    for (int i = 0; i < numBibliotecarios; i++) {
        printf("ID: %d | Nome: %s\n", bibliotecarios[i].id, bibliotecarios[i].nome);
    }
}

void atualizarBibliotecario() {
    limparTela();
    lerBibliotecarios();
    int id;
    printf("0. Cancelar\n");
    printf("\nDigite o ID do Bibliotecario para atualizar: ");
    scanf("%d", &id);
    
    if (id > 0 && id <= numBibliotecarios) {
        printf("Novo nome do Bibliotecario: ");
        scanf(" %[^\n]", bibliotecarios[id - 1].nome);
        printf("Bibliotecario atualizado com sucesso!\n");
    } else {
        printf("Bibliotecario nao encontrado.\n");
    }
     limparTela();
}

void deletarBibliotecario() {
    int id;
    printf("Digite o ID do Bibliotecario para deletar: ");
    printf("0. Cancelar\n");
    scanf("%d", &id);
    
    if (id > 0 && id <= numBibliotecarios) {
        for (int i = id - 1; i < numBibliotecarios - 1; i++) {
            bibliotecarios[i] = bibliotecarios[i + 1];
        }
        numBibliotecarios--;
        printf("Bibliotecario deletado com sucesso!\n");
    } else {
        printf("Bibliotecario nao encontrado.\n");
    }
}

// Funções CRUD para Clientes
void criarCliente() {
    if (numClientes < MAX_CLIENTES) {
        clientes[numClientes].id = numClientes + 1;
        printf("Nome do Cliente: ");
        printf("0. Cancelar\n");
        scanf(" %[^\n]", clientes[numClientes].nome);
        numClientes++;
        printf("Cliente cadastrado com sucesso!\n");
    } else {
        printf("Limite de clientes atingido.\n");
    }
}

void lerClientes() {
    printf("Clientes cadastrados:\n");
    for (int i = 0; i < numClientes; i++) {
        printf("ID: %d | Nome: %s\n", clientes[i].id, clientes[i].nome);
    }
}

void atualizarCliente() {
    int id;
    printf("Digite o ID do Cliente para atualizar: ");
    printf("0. Cancelar\n");
    scanf("%d", &id);
    
    if (id > 0 && id <= numClientes) {
        printf("Novo nome do Cliente: ");
        scanf(" %[^\n]", clientes[id - 1].nome);
        printf("Cliente atualizado com sucesso!\n");
    } else {
        printf("Cliente nao encontrado.\n");
    }
}

void deletarCliente() {
    int id;
    printf("Digite o ID do Cliente para deletar: ");
    printf("0. Cancelar\n");
    scanf("%d", &id);
    
    if (id > 0 && id <= numClientes) {
        for (int i = id - 1; i < numClientes - 1; i++) {
            clientes[i] = clientes[i + 1];
        }
        numClientes--;
        printf("Cliente deletado com sucesso!\n");
    } else {
        printf("Cliente nao encontrado.\n");
    }
}

// Funções CRUD para Livros
void criarLivro() {
    if (numLivros < MAX_LIVROS) {
        livros[numLivros].id = numLivros + 1;
        printf("Titulo do Livro: ");
        scanf(" %[^\n]", livros[numLivros].titulo);
        printf("Autor do Livro: ");
        scanf(" %[^\n]", livros[numLivros].autor);
        livros[numLivros].disponivel = 1;
        numLivros++;
        printf("Livro cadastrado com sucesso!\n");
    } else {
        printf("Limite de livros atingido.\n");
    }
}

void lerLivros() {
    printf("Livros cadastrados:\n");
    for (int i = 0; i < numLivros; i++) {
        printf("ID: %d | TTtulo: %s | Autor: %s | Disponivel: %s\n", 
            livros[i].id, livros[i].titulo, livros[i].autor, livros[i].disponivel ? "Sim" : "Não");
    }
}

void atualizarLivro() {
    int id;
    printf("Digite o ID do Livro para atualizar: ");
    scanf("%d", &id);
    printf("0. Cancelar\n");
    
    if (id > 0 && id <= numLivros) {
        printf("Novo titulo do Livro: ");
        scanf(" %[^\n]", livros[id - 1].titulo);
        printf("Novo autor do Livro: ");
        scanf(" %[^\n]", livros[id - 1].autor);
        printf("Livro atualizado com sucesso!\n");
    } else {
        printf("Livro nao encontrado.\n");
    }
}

void deletarLivro() {
    int id;
    printf("Digite o ID do Livro para deletar: ");
    scanf("%d", &id);
    
    if (id > 0 && id <= numLivros) {
        for (int i = id - 1; i < numLivros - 1; i++) {
            livros[i] = livros[i + 1];
        }
        numLivros--;
        printf("Livro deletado com sucesso!\n");
    } else {
        printf("Livro nao encontrado.\n");
    }
}

// Funções CRUD para Empréstimos
void criarEmprestimo() {
    if (numEmprestimos < MAX_EMPRESTIMOS) {
        int idCliente, idLivro;
        lerLivros();
        printf("Digite o ID do Cliente: ");
        scanf("%d", &idCliente);
        printf("Digite o ID do Livro: ");
        scanf("%d", &idLivro);
        
        if (livros[idLivro - 1].disponivel == 1) {
            emprestimos[numEmprestimos].id = numEmprestimos + 1;
            emprestimos[numEmprestimos].idCliente = idCliente;
            emprestimos[numEmprestimos].idLivro = idLivro;
            emprestimos[numEmprestimos].dataRetirada = time(NULL);
            emprestimos[numEmprestimos].diasEmprestimo = DIAS_LIMITE;
            livros[idLivro - 1].disponivel = 0;
            numEmprestimos++;
            printf("Emprestimo registrado com sucesso!\n");
        } else {
            printf("Livro nao disponivel.\n");
        }
    } else {
        printf("Limite de emprestimos atingido.\n");
    }
}

void lerEmprestimos() {
    printf("Emprestimos registrados:\n");
    for (int i = 0; i < numEmprestimos; i++) {
        printf("ID: %d | Cliente: %s | Livro: %s | Dias de Emprestimo: %d\n", 
            emprestimos[i].id, clientes[emprestimos[i].idCliente - 1].nome, 
            livros[emprestimos[i].idLivro - 1].titulo, emprestimos[i].diasEmprestimo);
    }
}

// Funções para Devolução de Livro
void devolverLivro() {
    int idEmprestimo;
    printf("Digite o ID do Emprestimo: ");
    scanf("%d", &idEmprestimo);

    if (idEmprestimo > 0 && idEmprestimo <= numEmprestimos) {
        time_t agora = time(NULL);
        double diasPassados = difftime(agora, emprestimos[idEmprestimo - 1].dataRetirada) / (60 * 60 * 24);

        if (diasPassados > DIAS_LIMITE) {
            double multa = (diasPassados - DIAS_LIMITE) * valorMultaPorDia;
            printf("Livro devolvido com atraso. Multa a ser paga: R$ %.2f\n", multa);
        } else {
            printf("Livro devolvido no prazo.\n");
        }

        livros[emprestimos[idEmprestimo - 1].idLivro - 1].disponivel = 1;
        printf("Devolucao registrada com sucesso!\n");
    } else {
        printf("Emprestimo nao encontrado.\n");
    }
}

// Função para Gerar Relatório
void gerarRelatorio() {
    printf("Relatorio de todos os registros:\n");
    lerBibliotecarios();
    lerClientes();
    lerLivros();
    lerEmprestimos();
}

// Submenus de cada entidade
void submenuBibliotecario() {
    int opcao;
    do {
        printf("\n--- Menu Bibliotecario ---\n");
        printf("1. Criar Bibliotecario\n");
        printf("2. Ler Bibliotecarios\n");
        printf("3. Atualizar Bibliotecario\n");
        printf("4. Deletar Bibliotecario\n");
        printf("0. Voltar\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1: criarBibliotecario(); break;
            case 2: lerBibliotecarios(); break;
            case 3: atualizarBibliotecario(); break;
            case 4: deletarBibliotecario(); break;
            case 0: break;
            default: printf("Opcao invalida!\n");
        }
    } while (opcao != 0);
     limparTela();
}

void submenuCliente() {
    int opcao;
    limparTela();
    do {
        printf("\n--- Menu Cliente ---\n");
        printf("1. Criar Cliente\n");
        printf("2. Ler Clientes\n");
        printf("3. Atualizar Cliente\n");
        printf("4. Deletar Cliente\n");
        printf("0. Voltar\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1: criarCliente(); break;
            case 2: lerClientes(); break;
            case 3: atualizarCliente(); break;
            case 4: deletarCliente(); break;
            case 0: break;
            default: printf("Opcao invalida!\n");
        }
    } while (opcao != 0);
}

void submenuLivro() {
    int opcao;
    limparTela();
    do {
        printf("\n--- Menu Livro ---\n");
        printf("1. Criar Livro\n");
        printf("2. Ler Livros\n");
        printf("3. Atualizar Livro\n");
        printf("4. Deletar Livro\n");
        printf("0. Voltar\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1: criarLivro(); break;
            case 2: lerLivros(); break;
            case 3: atualizarLivro(); break;
            case 4: deletarLivro(); break;
            case 0: break;
            default: printf("Opcao invalida!\n");
        }
    } while (opcao != 0);
}

void submenuEmprestimo() {
    int opcao;
    limparTela();
    do {
        printf("\n--- Menu Emprestimo ---\n");
        printf("1. Criar Emprestimo\n");
        printf("2. Ler Emprestimos\n");
        printf("0. Voltar\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1: criarEmprestimo(); break;
            case 2: lerEmprestimos(); break;
            case 0: break;
            default: printf("Opcao invalida!\n");
        }
    } while (opcao != 0);
}

// Menu Principal
void menu() {
    int opcao;
    do {
        limparTela();  // Limpa a tela antes de exibir o menu principal
        printf("********************************************\n");
        printf("*                                          *\n");
        printf("*    Bem-vindo ao Sistema de Biblioteca!   *\n");
        printf("*                                          *\n");
        printf("*     PIM - 2 Semestre - UNIP Sorocaba     *\n");
        printf("*                                          *\n");
        printf("********************************************\n");
        printf("\n");
        printf("1. Menu Bibliotecario\n");
        printf("2. Menu Cliente\n");
        printf("3. Menu Livro\n");
        printf("4. Menu Emprestimo\n");
        printf("5. Devolucao de Livro\n");
        printf("6. Gerar Relatorio\n");
        printf("0. Sair\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        limparTela();

        switch (opcao) {
            case 1: submenuBibliotecario(); break;
            case 2: submenuCliente(); break;
            case 3: submenuLivro(); break;
            case 4: submenuEmprestimo(); break;
            case 5: devolverLivro(); break;
            case 6: gerarRelatorio(); break;
            case 0: printf("Saindo...\n"); break;
            default: printf("Opção invalida!\n");
        }
    } while (opcao != 0);
}


int main() {
    setlocale(LC_ALL,"");
    menu();
    return 0;
}