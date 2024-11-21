- 👋 Hi, I’m @sigrioy
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
sigrioy/sigrioy is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

dot = Digraph(comment='Exphil Tankekart - Utfyllende', format='pdf')
dot.attr(rankdir='LR', size='12')

# Opprette hovedtemaer
main_themes = [
    "Nihilisme", "Kapitalisme", "Kompabilitisme", "Liberalisme", "Determinisme",
    "Geosentrisk verdensbilde", "Teleologisk natursyn", "Vitenskap og metode",
    "Normativ etikk", "Politisk filosofi", "Epistemologi", "Teknologi og samfunn"
]

for theme in main_themes:
    dot.node(theme, theme, shape='ellipse', style='filled', color='lightblue')

# Koble temaer til underbegreper og personer
connections = {
    "Nihilisme": [
        ("Thrasymachos", "Platon"), 
        ("Relativisme", ""), 
        ("Objektiv moral", "Sokrates/Platon")
    ],
    "Kapitalisme": [
        ("Karl Marx", ""), 
        ("Kapital og arbeid", ""), 
        ("Økonomisk ulikhet", "")
    ],
    "Kompabilitisme": [
        ("Fri vilje og determinisme", ""), 
        ("David Hume", ""), 
        ("Immanuel Kant", "")
    ],
    "Liberalisme": [
        ("Politisk frihet", "John Stuart Mill"), 
        ("Skadeprinsippet", ""), 
        ("Paternalisme", "")
    ],
    "Determinisme": [
        ("Fysisk kausalitet", ""), 
        ("Pierre-Simon Laplace", "")
    ],
    "Geosentrisk verdensbilde": [
        ("Kopernikus", ""), 
        ("Heliosentrisk skifte", "")
    ],
    "Teleologisk natursyn": [
        ("Aristoteles", ""), 
        ("Formål i naturen", "")
    ],
    "Vitenskap og metode": [
        ("Hypotetisk-deduktiv metode", "Popper"), 
        ("Thomas Kuhn", "Paradigmer")
    ],
    "Normativ etikk": [
        ("Pliktetikk", "Kant"), 
        ("Utilitarisme", "Mill"), 
        ("Dydsetikk", "Aristoteles")
    ],
    "Politisk filosofi": [
        ("Politisk realisme", "Hobbes"), 
        ("Politisk frihet: ikke-dominans", ""), 
        ("Rettighetsteorier", "")
    ],
    "Epistemologi": [
        ("Sannhet og kunnskap", ""), 
        ("Realisme", ""), 
        ("Relativisme", "")
    ],
    "Teknologi og samfunn": [
        ("Funksjonalisme", ""), 
        ("Sosiotekniske nettverk", ""), 
        ("Teknologisk instrumentalisme", "")
    ]
}

# Legge til koblinger
for theme, links in connections.items():
    for sub, person in links:
        sub_label = f"{sub}\n({person})" if person else sub
        dot.node(sub, sub_label, shape='box', style='filled', color='lightyellow')
        dot.edge(theme, sub)

# Eksportere grafen til PDF
output_path = '/mnt/data/Exphil_Tankekart_Endelig.pdf'
dot.render(output_path, view=False)
output_path
