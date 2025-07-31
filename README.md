# Sailing-martimport { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { motion } from "framer-motion";

const sampleProducts = [ { name: "Wireless Headphones", price: "$59.99", image: "https://picsum.photos/seed/headphones/300", }, { name: "Smart Watch", price: "$129.99", image: "https://picsum.photos/seed/watch/300", }, { name: "Portable Speaker", price: "$89.99", image: "https://picsum.photos/seed/speaker/300", }, { name: "Gaming Mouse", price: "$49.99", image: "https://picsum.photos/seed/mouse/300", }, { name: "Sunglasses", price: "$19.99", image: "https://picsum.photos/seed/sunglasses/300", }, { name: "Backpack", price: "$39.99", image: "https://picsum.photos/seed/backpack/300", }, ];

export default function PriiiMart() { const [products, setProducts] = useState(() => [...sampleProducts].sort(() => Math.random() - 0.5) );

const shuffleProducts = () => { setProducts([...sampleProducts].sort(() => Math.random() - 0.5)); };

return ( <div className="min-h-screen bg-gradient-to-br from-purple-900 via-black to-gray-900 text-white p-6"> <div className="max-w-7xl mx-auto"> <h1 className="text-4xl font-bold text-center mb-6 tracking-wide"> Welcome to <span className="text-purple-400">PriiiMart</span> </h1>

<div className="flex justify-center mb-6">
      <Button
        className="bg-purple-700 hover:bg-purple-600 text-white"
        onClick={shuffleProducts}
      >
        Shuffle Products
      </Button>
    </div>

    <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
      {products.map((product, index) => (
        <motion.div
          key={index}
          whileHover={{ scale: 1.05 }}
          whileTap={{ scale: 0.95 }}
          initial={{ opacity: 0, y: 40 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.4, delay: index * 0.1 }}
        >
          <Card className="bg-gray-800 border-gray-700 rounded-2xl shadow-lg">
            <img
              src={product.image}
              alt={product.name}
              className="rounded-t-2xl w-full h-52 object-cover"
            />
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-2 text-purple-300">
                {product.name}
              </h2>
              <p className="text-lg mb-4">{product.price}</p>
              <Button className="bg-purple-600 hover:bg-purple-500 w-full">
                Buy Now
              </Button>
            </CardContent>
          </Card>
        </motion.div>
      ))}
    </div>
  </div>
</div>

); }

