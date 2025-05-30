import random

class Personagem:
    def __init__(self, nome, classe, vida, ataque, defesa):
        self.nome = nome
        self.classe = classe
        self.vida = vida
        self.ataque = ataque
        self.defesa = defesa

    def atacar(self, inimigo):
        dano = max(0, self.ataque - inimigo.defesa + random.randint(-5, 5))
        inimigo.vida -= dano
        print(f"{self.nome} atacou {inimigo.nome} e causou {dano} de dano!")
        if inimigo.vida <= 0:
            print(f"{inimigo.nome} foi derrotado!")

    def curar(self):
        cura = random.randint(10, 20)
        self.vida += cura
        print(f"{self.nome} se curou em {cura} pontos de vida!")

    def esta_vivo(self):
        return self.vida > 0

class Inimigo:
    def __init__(self, nome, vida, ataque, defesa):
        self.nome = nome
        self.vida = vida
        self.ataque = ataque
        self.defesa = defesa

    def atacar(self, jogador):
        dano = max(0, self.ataque - jogador.defesa + random.randint(-5, 5))
        jogador.vida -= dano
        print(f"{self.nome} atacou {jogador.nome} e causou {dano} de dano!")

    def esta_vivo(self):
        return self.vida > 0

def criar_personagem():
    print("Escolha sua classe:")
    print("1. Guerreiro")
    print("2. Mago")
    print("3. Arqueiro")
    escolha = input("Digite o número da classe: ")

    nome = input("Digite o nome do personagem: ")

    if escolha == "1":
        return Personagem(nome, "Guerreiro", 100, 15, 10)
    elif escolha == "2":
        return Personagem(nome, "Mago", 80, 20, 5)
    elif escolha == "3":
        return Personagem(nome, "Arqueiro", 90, 18, 7)
    else:
        print("Opção inválida! Criando um Guerreiro por padrão.")
        return Personagem(nome, "Guerreiro", 100, 15, 10)

def combate(jogador, inimigo):
    while jogador.esta_vivo() and inimigo.esta_vivo():
        print(f"\n{jogador.nome} ({jogador.vida} HP) vs {inimigo.nome} ({inimigo.vida} HP)")
        print("1. Atacar")
        print("2. Curar")
        acao = input("O que deseja fazer? ")

        if acao == "1":
            jogador.atacar(inimigo)
        elif acao == "2":
            jogador.curar()
        else:
            print("Ação inválida! Você perdeu a vez.")

        if inimigo.esta_vivo():
            inimigo.atacar(jogador)

    if jogador.esta_vivo():
        print(f"\n{jogador.nome} venceu a batalha!")
    else:
        print(f"\n{jogador.nome} foi derrotado...")

# Iniciar o jogo
print("Bem-vindo ao RPG Simples!")
jogador = criar_personagem()
inimigo = Inimigo("Slime", 50, 10, 5)  # Inimigo básico
combate(jogador, inimigo)
