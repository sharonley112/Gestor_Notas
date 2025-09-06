# Gestor_Notas
Registro y visualización de notas cálculo de promedio
# ---------------------------------------------
# Sistema de registro de notas por curso
# ---------------------------------------------

# Lista de cursos predefinidos
cursos = ["Algoritmos", "Álgebra Lineal", "Precálculo", "Contabilidad", "Matemática Discreta"]

# Lista de notas precargadas
notas = [75, 80, 65, 90, 97]

# ---------------------------------------------
# Función para calcular el promedio
# ---------------------------------------------
def calcular_promedio():
    suma = 0
    contador = 0
    for nota in notas:
        suma += nota
        contador += 1
    return suma / contador if contador > 0 else 0

# ---------------------------------------------
# Función para actualizar notas (búsqueda lineal)
# ---------------------------------------------
def actualizar_nota():
    print("\n--- Actualización de Notas ---")
    curso_buscar = input("Ingrese el nombre del curso a actualizar: ").strip()

    # Búsqueda lineal
    encontrado = False
    for i in range(len(cursos)):
        if cursos[i].lower() == curso_buscar.lower():
            encontrado = True
            print(f"Nota actual de {cursos[i]}: {notas[i]}")
            while True:
                try:
                    nueva_nota = float(input("Ingrese la nueva nota (0-100): "))
                    if 0 <= nueva_nota <= 100:
                        notas[i] = nueva_nota
                        print(f" Nota de {cursos[i]} actualizada correctamente.")
                        break
                    else:
                        print(" Error: La nota debe estar entre 0 y 100.")
                except ValueError:
                    print(" Error: Debe ingresar un número válido.")
            break
    
    if not encontrado:
        print(" Curso no encontrado. Verifique el nombre.")

# ---------------------------------------------
# Mostrar notas registradas
# ---------------------------------------------
print("\n Notas registradas:")
for i in range(len(cursos)):
    print(f"{cursos[i]}: {notas[i]}")

# Mostrar promedio
promedio = calcular_promedio()
print(f"\n Promedio general: {promedio:.2f}")

# Opción de actualización
while True:
    opcion = input("\n¿Desea actualizar alguna nota? (s/n): ").strip().lower()
    if opcion == "s":
        actualizar_nota()
        promedio = calcular_promedio()
        print(f"\n Nuevo promedio general: {promedio:.2f}")
    elif opcion == "n":
        print("\n Programa finalizado.")
        break
    else:
        print(" Opción no válida. Intente de nuevo.")

